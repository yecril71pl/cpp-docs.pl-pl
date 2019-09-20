---
title: Obsługa wyjątków strukturalnych w języku C++
description: Jak obsługiwać wyjątki strukturalne przy użyciu C++ modelu obsługi wyjątków.
ms.date: 09/19/2019
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 0c0e458f576325034d77676d247020adedfa33e5
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158738"
---
# <a name="handle-structured-exceptions-in-c"></a>Obsługa wyjątków strukturalnych w języku C++

Główna różnica między obsługą wyjątków strukturalnych C (SEH) i C++ obsługą wyjątków polega na C++ tym, że model obsługi wyjątków zajmuje się typami, podczas gdy model obsługi wyjątków strukturalnych C zajmuje się wyjątkami jednego typu; w specjalnej postaci **bez znaku int**. Oznacza to, że wyjątki C są identyfikowane przez nieoznaczoną wartość całkowitą, natomiast wyjątki C++ są identyfikowane przez typ danych. Gdy wyjątek strukturalny jest wywoływany w języku C, każda możliwa obsługa wykonuje filtr, który sprawdza kontekst wyjątku C i określa, czy należy zaakceptować wyjątek, przekazać go do innego programu obsługi lub zignorować. Gdy wyjątek jest zgłaszany w języku C++, może być dowolnego typu.

Druga różnica polega na tym, że model obsługi wyjątków strukturalnych C jest określany jako *asynchroniczny*, ponieważ wyjątki występują jako pomocnicze dla normalnego przepływu sterowania. Mechanizm C++ obsługi wyjątków jest w pełni *synchroniczny*, co oznacza, że wyjątki występują tylko wtedy, gdy są zgłaszane.

W przypadku korzystania z opcji kompilatora [/EHS lub/EHsc](../build/reference/eh-exception-handling-model.md) żadne programy C++ obsługi wyjątków nie obsługują wyjątków strukturalnych. Te wyjątki są obsługiwane tylko przez program obsługi wyjątków strukturalnych **__except** lub programy obsługi zakończenia strukturalnego **__finally** . Aby uzyskać więcej informacji, zobacz [strukturalna obsługa wyjątkówC++(C/)](structured-exception-handling-c-cpp.md).

W przypadku opcji kompilatora [/EHa](../build/reference/eh-exception-handling-model.md) , jeśli wyjątek C jest wywoływany w C++ programie, może być obsługiwany przez procedurę obsługi wyjątków strukturalnych ze skojarzonym filtrem lub przez C++ program obsługi **catch** , w zależności od tego, który jest dynamicznie zbliżony do wyjątku Context. Na przykład ten przykładowy C++ program zgłasza wyjątek C wewnątrz C++ kontekstu **try** :

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>Przykład — Przechwyć wyjątek C w bloku C++ catch

```cpp
// exceptions_Exception_Handling_Differences.cpp
// compile with: /EHa
#include <iostream>

using namespace std;
void SEHFunc( void );

int main() {
   try {
      SEHFunc();
   }
   catch( ... ) {
      cout << "Caught a C exception."<< endl;
   }
}

void SEHFunc() {
   __try {
      int x, y = 0;
      x = 5 / y;
   }
   __finally {
      cout << "In finally." << endl;
   }
}
```

```Output
In finally.
Caught a C exception.
```

## <a name="c-exception-wrapper-classes"></a>Klasy otoki wyjątków języka C

W prostym przykładzie podobnym do powyższego wyjątek C może być przechwytywany tylko przez wielokropek ( **...** ) Procedura obsługi **catch** . Brak informacji na temat typu lub rodzaju wyjątku jest przekazywany do modułu obsługi. Chociaż ta metoda działa, w niektórych przypadkach może być konieczne zdefiniowanie transformacji między dwoma modelami obsługi wyjątków, aby każdy wyjątek C był skojarzony z konkretną klasą. Aby przekształcić jeden, można zdefiniować klasę "otoka" wyjątku języka C, która może być używana lub pochodna w celu podzielenia określonego typu klasy na wyjątek C. Dzięki temu każdy wyjątek C może być obsługiwany oddzielnie przez określony C++ program obsługi **catch** , a nie wszystkie z nich w ramach jednej procedury obsługi.

Klasa otoki może mieć interfejs składający się z niektórych funkcji składowych, które określają wartość wyjątku i dostęp do rozszerzonych informacji kontekstu wyjątku dostarczonych przez model wyjątków C. Można również zdefiniować konstruktora domyślnego i konstruktora, który akceptuje argument **int bez znaku** (aby zapewnić podstawową reprezentację wyjątku C) i bitowego konstruktora kopiującego. Oto możliwa implementacja klasy otoki wyjątków C:

```cpp
// exceptions_Exception_Handling_Differences2.cpp
// compile with: /c
class SE_Exception {
private:
   SE_Exception() {}
   SE_Exception( SE_Exception& ) {}
   unsigned int nSE;
public:
   SE_Exception( unsigned int n ) : nSE( n ) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() {
      return nSE;
   }
};
```

Aby użyć tej klasy, zainstaluj funkcję translacji wyjątków niestandardowych języka C, która jest wywoływana przez mechanizm obsługi wyjątków wewnętrznych za każdym razem, gdy zostanie zgłoszony wyjątek C. W ramach funkcji tłumaczenia można zgłosić dowolny `SE_Exception` wyjątek typu (być może typ lub typ klasy pochodzący z `SE_Exception`), który może zostać przechwycony przez odpowiednią pasującą C++ procedurę obsługi **catch** . Funkcja tłumaczenia może zamiast tego zwracać wartość, co oznacza, że nie obsłużył wyjątku. Jeśli sama funkcja tłumaczenia zgłasza wyjątek C, zostanie wywołana [przerwa](../c-runtime-library/reference/terminate-crt.md) .

Aby określić niestandardową funkcję tłumaczenia, wywołaj funkcję [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) z nazwą funkcji tłumaczenia jako jej pojedynczy argument. Funkcja tłumaczenia, którą można napisać, jest wywoływana jednokrotnie dla każdego wywołania funkcji na stosie, który ma bloki **try** . Nie istnieje domyślna Funkcja tłumaczenia; Jeśli nie określisz go przez wywołanie **_set_se_translator**, wyjątek C może być przechwytywany tylko przez procedurę obsługi **catch** z wielokropkiem.

## <a name="example---use-a-custom-translation-function"></a>Przykład — używanie niestandardowej funkcji tłumaczenia

Na przykład, poniższy kod instaluje niestandardową funkcję tłumaczenia i następnie zgłasza wyjątek C, który jest otoczony przez klasę `SE_Exception`:

```cpp
// exceptions_Exception_Handling_Differences3.cpp
// compile with: /EHa
#include <stdio.h>
#include <eh.h>
#include <windows.h>

class SE_Exception {
private:
   SE_Exception() {}
   unsigned int nSE;
public:
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}
   SE_Exception(unsigned int n) : nSE(n) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() { return nSE; }
};

void SEFunc() {
    __try {
        int x, y = 0;
        x = 5 / y;
    }
    __finally {
        printf_s( "In finally\n" );
    }
}

void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {
    printf_s( "In trans_func.\n" );
    throw SE_Exception( u );
}

int main() {
    _set_se_translator( trans_func );
    try {
        SEFunc();
    }
    catch( SE_Exception e ) {
        printf_s( "Caught a __try exception with SE_Exception.\n" );
        printf_s( "nSE = 0x%x\n", e.getSeNumber() );
    }
}
```

```Output
In trans_func.
In finally
Caught a __try exception with SE_Exception.
nSE = 0xc0000094
```

## <a name="see-also"></a>Zobacz także

[Mieszanie języka C (Structured) C++ i wyjątków](../cpp/mixing-c-structured-and-cpp-exceptions.md)
