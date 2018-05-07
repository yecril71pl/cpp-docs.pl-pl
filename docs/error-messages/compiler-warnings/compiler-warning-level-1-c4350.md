---
title: Kompilatora (poziom 1) ostrzeżenie C4350 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7e13b73eeee9c24841e97419b702b3e41be3982
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4350"></a>Kompilator C4350 ostrzegawcze (poziom 1)
zmiana zachowania: wywołano element członkowski 'członek1' zamiast 'członek2'  
  
 Odwołanie niestałe nie może być powiązany r-wartości. W wersjach programu Visual C++ przed Visual Studio 2003 było powiązać r-wartości z odwołaniem do wartości niestałej w bezpośredniego inicjowania. Ten kod zawiera teraz ostrzeżenie.  
  
 W celu zapewnienia zgodności z poprzednimi wersjami jest nadal możliwe powiązać rvalues odwołania do wartości niestałej, ale konwersje standardowe są preferowane w przypadku, gdy jest to możliwe.  
  
 To ostrzeżenie reprezentuje zmianę zachowania kompilatora Visual C++ .NET 2002. Jeśli włączone, to ostrzeżenie można prawdopodobnie należy podać prawidłowy kod. Na przykład może być podane przy użyciu **std::auto_ptr** szablonu klasy.  
  
 Jeśli to ostrzeżenie, sprawdź swój kod, aby sprawdzić, czy zależy od rvalues powiązania do wartości niestałej odwołań. Dodawanie odwołania do typu const lub zapewniając dodatkowe przeciążenia odwołanie niestałe może rozwiązać ten problem.  
  
 To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Poniższy przykład generuje C4350:  
  
```cpp  
// C4350.cpp  
// compile with: /W1  
#pragma warning (default : 4350)  
class A {};  
  
class B  
{  
public:  
   B(B&){}  
   // try the following instead:  
   // B(const B&){}  
  
   B(A){}  
   operator A(){ return A();}  
};  
  
B source() { return A(); }  
  
int main()  
{  
   B ap(source());   // C4350  
}  
```