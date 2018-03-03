---
title: "Kompilatora (poziom 1) ostrzeżenie C4743 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4743
dev_langs:
- C++
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a7169afdf7fb4c9a03e509f0332e738a66a06f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4743"></a>Kompilator C4743 ostrzegawcze (poziom 1)
"*typu*"ma inny rozmiar "*file1*"i"*plik2*": *numer* i *numer* bajtów  
  
 Zewnętrzne zmienna zdefiniowana w dwóch plikach lub odwołuje się ma różne typy w tych plikach, a kompilator ustali, że rozmiar zmiennej w *file1* różni się od rozmiaru zmiennej w *plik2*.  
  
 Jeśli to ostrzeżenie może być wysyłany dla języka C++ jest ważny przypadek. Jeśli te same typy o takiej samej nazwie w dwóch różnych plików, należy zadeklarować deklaracje te zawierają funkcje wirtualne, a deklaracji nie są takie same, kompilator może emitować ostrzeżenie C4744 dla tabele funkcji wirtualnych. To ostrzeżenie występuje, ponieważ istnieją dwie tabele różnych funkcji wirtualnej o rozmiarze dla tego samego typu i konsolidatora należy wybrać jeden z nich, aby dołączyć do pliku wykonywalnego.  Istnieje możliwość, że może to spowodować wywoływania funkcji wirtualnej niewłaściwy program.  
  
 Aby usunąć to ostrzeżenie, użyj tej samej definicji typu lub użyj innej nazwy dla typów lub zmienne.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera jedną definicję tego typu.  
  
```  
// C4743a.cpp  
// compile with: /c  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
};  
  
void C::f1(void) {}  
void C::f2(void) {}  
void C::f3(void) {}  
C q;  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4743.  
  
```  
// C4743b.cpp  
// compile with: C4743a.cpp /W1 /GL /O2  
// C4743 expected  
class C {  
public:  
    virtual void f1(void);  
    virtual void f2(void);  
    virtual void f3(void);  
    virtual void f4(void);  
    virtual void f5(void);  
};  
  
void C::f4(void) {}  
void C::f5(void) {}  
C x;  
  
int main() {}   
```