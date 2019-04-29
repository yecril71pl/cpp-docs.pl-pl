---
title: _set_se_translator
ms.date: 02/21/2018
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
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 18ee500d7b884d1934c29dc91d9bcb03d507680d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356553"
---
# <a name="setsetranslator"></a>_set_se_translator

Ustaw funkcję wywołania zwrotnego na wątek do translacji wyjątki Win32 (wyjątki strukturalne C) do C++ wpisane wyjątków.

## <a name="syntax"></a>Składnia

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Parametry

*seTransFunction*<br/>
Wskaźnik do C struktury funkcję tłumacza wyjątków, które piszesz.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniego funkcję tłumacza zarejestrowane przez **_set_se_translator**, dzięki czemu można później przywrócić poprzedniej funkcji. Jeśli żadna funkcja poprzedniej została ustawiona, wartość zwracana można przywrócić domyślne zachowanie; Ta wartość może być **nullptr**.

## <a name="remarks"></a>Uwagi

**_Set_se_translator** funkcja stanowi sposób obsługi wyjątków systemu Win32 (wyjątki strukturalne C) jako C++ kontrolą typów wyjątków. Aby zezwolić na każdy wyjątek C może być obsługiwanych przez C++ **catch** obsługi, należy najpierw zdefiniować klasa otoki wyjątek C, które mogą być używane lub pochodzący od atrybutu typu określonej klasy do wyjątku C. Aby użyć tej klasy, należy zainstalować niestandardowe funkcję do tłumacza wyjątków C, która jest wywoływana przez wewnętrzny mechanizm obsługi wyjątków, każdorazowo, gdy wyjątek C jest inicjowany. W ramach funkcji tłumaczenia, możliwe jest zgłoszenie wyjątku dowolnego typu, który może zostać przechwycony przez C++ zgodnego **catch** programu obsługi.

Należy użyć [/eha](../../build/reference/eh-exception-handling-model.md) przy użyciu **_set_se_translator**.

Aby określić niestandardową funkcję tłumaczenia, należy wywołać **_set_se_translator** przy użyciu nazwy funkcji tłumaczenia, jako argumentem. Napisana funkcja tłumaczenia jest wywoływana raz dla każdego wywołania funkcji na stosie, które ma **spróbuj** bloków. Nie ma domyślnego translator funkcji.

Funkcji w usłudze translator należy wykonać, nie więcej niż throw C++ wpisane wyjątku. Jeśli tak, nic, oprócz zgłaszanie (np. na przykład zapisywania do pliku dziennika) programu mogą nie zachowywać się zgodnie z oczekiwaniami, ponieważ liczba wywoływaną funkcję tłumacza jest zależny od platformy.

W środowisku wielowątkowym funkcjach tłumacza są przechowywane osobno dla każdego wątku. Każdy nowy wątek musi zainstalować jego własnej funkcji w usłudze translator. W związku z tym każdy wątek jest odpowiedzialny za własne tłumaczenia obsługi. **_set_se_translator** specyficzne dla jednego wątku; innej biblioteki DLL, można zainstalować funkcję tłumaczenia różne.

*SeTransFunction* napisana funkcja musi być funkcją natywnie skompilowanego (nie kompilowanych z/CLR). Należy wykonać liczbę całkowitą bez znaku i wskaźnik do systemu Win32 **_exception_pointers —** struktury jako argumenty. Argumenty są zwracane wartości wywołania funkcji API Win32 **GetExceptionCode** i **GetExceptionInformation** działa odpowiednio.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Dla **_set_se_translator**, istnieją implikacje dotyczące dynamicznego łączenia do CRT; innej biblioteki DLL w procesie mogą wywołać **_set_se_translator** i Zastąp programu obsługi swój własny.

Korzystając z **_set_se_translator** z kodu zarządzanego (kodu skompilowanego za pomocą/CLR) lub mieszany kodu natywnego i zarządzanego, należy pamiętać, że translator ma wpływ na wyjątki generowane tylko kodu natywnego. Żadnym zarządzanym wyjątków wygenerowanych w kodzie zarządzanym (np. podczas zgłaszania `System::Exception`) nie są przesyłane za pośrednictwem funkcji w usłudze translator. Wyjątki zgłoszone w kodzie zarządzanym przy użyciu funkcji Win32 **RaiseException** lub spowodowane przez wyjątek systemu, takie jak dzielenie przez zero wyjątków są przesyłane za pośrednictwem translator.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>
#include <exception>

class SE_Exception : public std::exception
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

Chociaż funkcje udostępniane przez **_set_se_translator** jest niedostępne w kodzie zarządzanym, jest możliwe do użycia tego mapowania w kodzie natywnym, nawet jeśli natywny kod znajduje się w kompilacji w ramach **/CLR** Przełącz tak długo, jak kod macierzysty jest sygnalizowany `#pragma unmanaged`. Jeśli wyjątek strukturalny został zgłoszony w zarządzanym kodzie, który ma być zmapowana, muszą być oznaczone jako kod, który generuje i obsługuje wyjątek `#pragma unmanaged`. Poniższy kod przedstawia możliwości zastosowania. Aby uzyskać więcej informacji, zobacz [dyrektywy Pragma i słowo kluczowe __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <assert.h>
#include <stdio.h>
#include <exception>

int thrower_func(int i) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception {
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception(unsigned int n) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

#pragma unmanaged
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS)
{
    throw SE_Exception(u);
}

void DoTest()
{
    try
    {
        thrower_func(10);
    }
    catch(SE_Exception& e)
    {
        printf("Caught SE_Exception, error %8.8x\n", e.getSeNumber());
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
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[Zakończenie](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
