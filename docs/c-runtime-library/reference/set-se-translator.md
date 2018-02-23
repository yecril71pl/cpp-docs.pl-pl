---
title: _set_se_translator | Microsoft Docs
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _set_se_translator
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _set_se_translator
- set_se_translator
dev_langs:
- C++
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5b5eec59acfe65189368a9b0555c3065b7159aae
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2018
---
# <a name="setsetranslator"></a>_set_se_translator

Ustaw wyjątki wpisane funkcję wywołania zwrotnego dla każdego wątku tłumaczenie Win32 wyjątków (C strukturalnych wyjątkami) w języku C++.

## <a name="syntax"></a>Składnia

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Parametry

*seTransFunction*  
Wskaźnik do C struktury funkcja translator wyjątek, czy możesz zapisywać.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniego funkcja translator zarejestrowany przez `_set_se_translator`, tak aby później można przywrócić poprzedniego funkcji. Jeśli nie ustawiono Brak poprzedniej funkcji, zwracana wartość można przywrócić domyślne zachowanie; Ta wartość może być **nullptr**.

## <a name="remarks"></a>Uwagi

`_set_se_translator` Funkcja zapewnia sposób obsługi wyjątków Win32 (C strukturalnych wyjątkami) jako C++ wpisane wyjątków. Aby umożliwić każdej wyjątek języka C do obsłużenia C++ `catch` obsługi, najpierw zdefiniować C klasy otoki wyjątków, które mogą być używane lub pochodzący od atrybutu typu określonej klasy wyjątek C. Aby korzystać z tej klasy, należy zainstalować niestandardowych C wyjątek translator funkcja jest wywoływana przez wewnętrzny mechanizm obsługi wyjątków zawsze, gdy wyjątek C. W ramach funkcji translator, może zgłosić dowolnego typu wyjątku, który może podlegać pasującego C++ `catch` obsługi.

Należy użyć [/eha](../../build/reference/eh-exception-handling-model.md) przy użyciu `_set_se_translator`.

Aby określić funkcję translacji niestandardowe, należy wywołać `_set_se_translator` przy użyciu nazwy funkcji tłumaczenia jako jej argument. Funkcja translator, który można zapisać jest wywoływana raz dla każdego wywołania funkcji na stosie, który ma `try` bloków. Nie istnieje żadna funkcja translator domyślne.

Funkcja translator należy wykonać, nie więcej niż throw C++ typu wyjątku. Jeśli tak, aby nic oprócz zgłaszanie (na przykład zapisywania do pliku dziennika, na przykład) program może nie działać zgodnie z oczekiwaniami, ponieważ liczba translator funkcja jest wywoływana jest zależny od platformy.

W środowisku wielowątkowym translator funkcje są obsługiwane osobno dla każdego wątku. Każdym nowym wątku, należy zainstalować ma własną funkcję translatora. W związku z tym każdy wątek jest odpowiedzialny za obchodzenie tłumaczenia. `_set_se_translator` jest przeznaczony dla jednego wątku; innej bibliotece DLL można zainstalować funkcję różnych tłumaczenia.

*SeTransFunction* funkcji, który można zapisać musi być funkcją natywnie skompilowanego (nie kompilowanych z/CLR). Należy wykonać całkowitą bez znaku i wskaźnika do systemu Win32 `_EXCEPTION_POINTERS` struktury jako argumenty. Argumenty są zwracane wartości z wywołania funkcji API Win32 `GetExceptionCode` i `GetExceptionInformation` funkcje odpowiednio.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Dla `_set_se_translator`, istnieją efekty podczas łączenia dynamicznie CRT; innego biblioteki DLL w procesie może wywołać `_set_se_translator` i Zastąp programu obsługi własny.

Korzystając z `_set_se_translator` z kodu zarządzanego (kodu skompilowanego za pomocą/CLR) lub mieszane kodu natywnego i zarządzanego, należy pamiętać, że translator ma wpływ na wyjątki generowane tylko kodu natywnego. Dowolny zarządzany wyjątki wygenerować w zarządzanym kodzie (takie jak kiedy wywoływanie `System::Exception`) nie są wysyłane za pośrednictwem funkcji translatora. Wyjątki zgłoszone w kodzie zarządzanym przy użyciu funkcji Win32 `RaiseException` lub spowodowane przez wyjątek systemu, takie jak dzielenie przez zero wyjątków są wysyłane za pośrednictwem translatora.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`_set_se_translator`|\<eh.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class SE_Exception
{
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception( unsigned int n ) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func(unsigned int u, EXCEPTION_POINTERS*)
{
    throw SE_Exception(u);
}

int main()
{
    auto original = _set_se_translator(trans_func); 
    try
    {
        SEFunc();
    }
    catch(SE_Exception& e)
    {
        printf("Caught a __try exception, error %8.8x.\n", e.getSeNumber());
    }
    _set_se_translator(original);
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Przykład

Chociaż funkcje udostępniane przez `_set_se_translator` jest niedostępne w kodzie zarządzanym, jest możliwość użycia tego mapowania w kodzie natywnym, nawet jeśli jest tego kodu natywnego w kompilacji, w obszarze `/clr` przełącznika tak długo, jak kod macierzysty jest sygnalizowany `#pragma unmanaged`. Jeśli strukturalnych wyjątek został zgłoszony w zarządzanym kodzie, który ma być zmapowana, muszą być oznaczone jako kod, który generuje i obsługuje wyjątek `#pragma unmanaged`. Poniższy kod przedstawia możliwości zastosowania. Aby uzyskać więcej informacji, zobacz [dyrektywy Pragma i słowo kluczowe __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <assert.h>
#include <stdio.h>

int thrower_func(int i) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class CMyException{
private:
    unsigned int nSE;
public:
    CMyException() : nSE{ 0 } {}
    CMyException(unsigned int n) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

#pragma unmanaged
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS)
{
    throw CMyException(u);
}

void DoTest()
{
    try
    {
        thrower_func(10);
    }
    catch(CMyException e)
    {
        printf("Caught CMyException.\n");
    }
    catch(...)
    {
        printf("Caught unexpected SEH exception.\n");
    }
}
#pragma managed

int main() {
    auto original = _set_se_translator(my_trans_func);
    DoTest();
    _set_se_translator(original);
}
```

```Output
Caught CMyException, error c0000094
```

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)  
[set_terminate](../../c-runtime-library/reference/set-terminate-crt.md)  
[set_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)  
[Zakończenie](../../c-runtime-library/reference/terminate-crt.md)  
[Nieoczekiwany](../../c-runtime-library/reference/unexpected-crt.md)  
