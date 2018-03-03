---
title: Inicjalizacja CRT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d472026649bbe1d72a9afba42f224b0b9159258d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crt-initialization"></a>Inicjalizacja CRT
W tym temacie opisano, jak CRT inicjuje globalne stanów w kodzie natywnym.  
  
 Domyślnie konsolidator obejmuje biblioteki CRT, która udostępnia własny kod uruchomienia. Ten kod startowy inicjuje biblioteki CRT, wywołuje inicjatory globalne, a następnie wywołuje dostarczane przez użytkownika `main` funkcja dla aplikacji konsoli.  
  
## <a name="initializing-a-global-object"></a>Inicjowanie obiektu globalnego  
 Rozważmy następujący kod:  
  
```  
int func(void)  
{  
    return 3;  
}  
  
int gi = func();  
  
int main()  
{  
    return gi;  
}  
```  
  
 Według standardu C/C++ `func()` musi zostać wywołana przed `main()` jest wykonywana. Ale który wywołuje ona?  
  
 Aby określić, to aby ustawić punkt przerwania w `func()`, debugowania aplikacji i sprawdzić stosu. Jest to możliwe, ponieważ kod źródłowy CRT jest dołączana do programu Visual Studio.  
  
 Podczas przeglądania funkcji na stosie, można znaleźć czy CRT jest lista wskaźników funkcji w pętli i wywoływanie każdego z nich, po ich napotkaniu. Te funkcje są podobne do `func()` lub konstruktory wystąpień klas.  
  
 CRT uzyskuje listę wskaźników funkcji kompilatora Visual C++. Kompilator widzi inicjatorze globalnym, generuje dynamiczne inicjator w `.CRT$XCU` sekcji (gdzie `CRT` jest nazwy sekcji i `XCU` to nazwa grupy). Aby uzyskać listę tych inicjatorów dynamicznych, uruchom polecenie **dumpbin/all main.obj**, a następnie wyszukaj `.CRT$XCU` sekcji (jeśli main.cpp jest skompilowana jako plik C++ nie jest plikiem C). Będzie podobny do następującego:  
  
```  
SECTION HEADER #6  
.CRT$XCU name  
       0 physical address  
       0 virtual address  
       4 size of raw data  
     1F2 file pointer to raw data (000001F2 to 000001F5)  
     1F6 file pointer to relocation table  
       0 file pointer to line numbers  
       1 number of relocations  
       0 number of line numbers  
40300040 flags  
         Initialized Data  
         4 byte align  
         Read Only  
  
RAW DATA #6  
  00000000: 00 00 00 00                                      ....  
  
RELOCATIONS #6  
                                                Symbol    Symbol  
 Offset    Type              Applied To         Index     Name  
 --------  ----------------  -----------------  --------  ------  
 00000000  DIR32                      00000000         C  ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))  
```  
  
 CRT definiuje dwóch wskaźników:  
  
-   `__xc_a`w`.CRT$XCA`  
  
-   `__xc_z`w`.CRT$XCZ`  
  
 Zarówno grupy nie mają inne symbole zdefiniowane z wyjątkiem `__xc_a` i `__xc_z`.  
  
 Teraz, kiedy konsolidator odczytuje różnych `.CRT` grupy go łączy je w jedną sekcję i porządkuje je alfabetycznie. Oznacza to, że inicjatory globalne zdefiniowane przez użytkownika (który umieszcza kompilatora Visual C++ `.CRT$XCU`) będzie zawsze występować po `.CRT$XCA` i przed `.CRT$XCZ`.  
  
 Sekcja będzie podobny do następującego:  
  
```  
.CRT$XCA  
            __xc_a  
.CRT$XCU  
            Pointer to Global Initializer 1  
            Pointer to Global Initializer 2  
.CRT$XCZ  
            __xc_z  
```  
  
 Tak, biblioteka CRT używa zarówno `__xc_a` i `__xc_z` ustalenie początek i koniec listy inicjatorów globalnych ze względu na sposób, w którym one zostały przedstawione w pamięci po załadowaniu obrazu.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)