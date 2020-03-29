---
title: 对象生存期和资源管理（RAII）
description: 按照新式C++中的 RAII 原则来避免资源泄漏。
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: 01867ec0a71ba54bb6534da1b408cb0610d652a7
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303370"
---
# <a name="object-lifetime-and-resource-management-raii"></a>对象生存期和资源管理（RAII）

C++与托管语言不同 ，没有自动*垃圾回收*。 这是在程序运行时释放堆内存和其他资源的内部过程。 C++程序负责将所有获取的资源返回到操作系统。 未能释放未使用的资源称为 "*泄漏*"。 在进程退出之前，泄漏的资源对其他程序不可用。 具体而言，内存泄漏是 C 样式编程中出现 bug 的一个常见原因。

新式C++通过在堆栈上声明对象，尽可能避免使用堆内存。 如果资源对于堆栈而言太大，则它应*归对象所有*。 初始化对象时，它将获取其拥有的资源。 然后，该对象负责在其析构函数中释放资源。 所属对象本身在堆栈上声明。 *对象拥有的资源*的原则也称为 "资源采集为初始化" 或 RAII。

当资源拥有的堆栈对象超出范围时，将自动调用其析构函数。 这样，中C++的垃圾回收与对象生存期密切相关，并且是确定性的。 资源始终在程序中的已知点释放，你可以对其进行控制。 仅类似 C++ 中的确定析构函数可公平处理内存和非内存资源。

下面的示例演示一个 `w`的简单对象。 它在函数作用域的堆栈上声明，并在函数块的末尾被销毁。 对象 `w` 不拥有任何*资源*（如堆分配的内存）。 它唯一的成员 `g` 是在堆栈上自行声明的，只是与 `w`一起超出范围。 `widget` 析构函数中无需任何特殊代码。

```cpp
class widget {
private:
    gadget g;   // lifetime automatically tied to enclosing object
public:
    void draw();
};

void functionUsingWidget () {
    widget w;   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.g gadget member
    // ...
    w.draw();
    // ...
} // automatic destruction and deallocation for w and w.g
  // automatic exception safety,
  // as if "finally { w.dispose(); w.g.dispose(); }"
```

在下面的示例中，`w` 拥有内存资源，因此必须在其析构函数中包含代码以删除内存。
 
```cpp
class widget
{
private:
    int* data;
public:
    widget(const int size) { data = new int[size]; } // acquire
    ~widget() { delete[] data; } // release
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                        // constructs w, including the w.data member
    w.do_something();

} // automatic destruction and deallocation for w and w.data

```

自 c + + 11 起，有一种更好的方法来编写前面的示例：使用标准库中的智能指针。 智能指针处理其拥有的内存分配和删除操作。 使用智能指针，无需在 `widget` 类中使用显式析构函数。

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

通过使用智能指针进行内存分配，可以消除内存泄漏的可能性。 此模型适用于其他资源，例如文件句柄或套接字。 你可以在类中以类似的方式管理自己的资源。 有关详细信息，请参阅[智能指针](smart-pointers-modern-cpp.md)。

当对象超出C++范围时，的设计可确保对象被销毁。 也就是说，它们被销毁为块，并按构造的相反顺序退出。 销毁对象时，将按特定顺序销毁其基项和成员。 在任何块以外的全局范围内声明的对象都可能导致问题。 如果全局对象的构造函数引发异常，则可能难以进行调试。

## <a name="see-also"></a>另请参阅

[欢迎返回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)
