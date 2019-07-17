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
ms.openlocfilehash: 23eb4e9016666567771832cefed686cb9197b02f
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299706"
---
# <a name="setsetranslator"></a>_set_se_translator

Ustaw funkcję wywołania zwrotnego dla wątku, aby przetłumaczyć wyjątki Win32 (wyjątki strukturalne C) na C++ wpisane wyjątki.

## <a name="syntax"></a>Składnia

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Parametry

*seTransFunction*<br/>
Wskaźnik do zapisanej funkcji translatora wyjątków języka C.

## <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do poprzedniej funkcji translatora zarejestrowanej przez **_set_se_translator**, aby można było przywrócić poprzednią funkcję. Jeśli żadna Poprzednia funkcja nie została ustawiona, wartość zwracana może zostać użyta do przywrócenia zachowania domyślnego. Ta wartość może być **nullptr**.

## <a name="remarks"></a>Uwagi

Funkcja **_set_se_translator** zapewnia sposób obsługi wyjątków Win32 (wyjątki strukturalne C) jako C++ wyjątków wpisanych. Aby zezwolić na obsługę każdego wyjątku c przez C++ procedurę obsługi **catch** , należy najpierw zdefiniować klasę otoki wyjątku c, która może być używana, lub pochodną klasy, aby przypisać do wyjątku typu c. Aby użyć tej klasy, należy zainstalować niestandardową funkcję translatora wyjątków języka C, która jest wywoływana przez wewnętrzny mechanizm obsługi wyjątków za każdym razem, gdy zostanie zgłoszony wyjątek C. W ramach funkcji translator można zgłosić każdy wpisany wyjątek, który może zostać przechwycony przez zgodną C++ procedurę obsługi **catch** .

W przypadku korzystania z **_set_se_translator**należy użyć [/EHa](../../build/reference/eh-exception-handling-model.md) .

Aby określić niestandardową funkcję tłumaczenia, należy wywołać **_set_se_translator** przy użyciu nazwy funkcji tłumaczenia jako argumentu. Funkcja translatora, którą można napisać, jest wywoływana jednokrotnie dla każdego wywołania funkcji na stosie, który ma bloki **try** . Brak domyślnej funkcji translatora.

Funkcja translatora nie powinna wykonywać więcej niż zgłosić wyjątek C++ z określonym typem. Jeśli to wszystko, oprócz wyrzucania (na przykład zapisu w pliku dziennika), program może nie zachowywać się zgodnie z oczekiwaniami, ponieważ liczba wywoływania funkcji translatora jest zależna od platformy.

W środowisku wielowątkowym funkcje usługi Translator są obsługiwane osobno dla każdego wątku. Każdy nowy wątek musi zainstalować własną funkcję translatora. W ten sposób każdy wątek jest odpowiedzialny za obsługę translacji. **_set_se_translator** jest charakterystyczny dla jednego wątku; inna Biblioteka DLL może zainstalować inną funkcję tłumaczenia.

Funkcja *seTransFunction* , którą pisze, musi być funkcją skompilowaną natywnie (nieskompilowana z/CLR). Musi ona przyjmować liczbę całkowitą bez znaku oraz wskaźnik do struktury **_EXCEPTION_POINTERS** Win32 jako argumenty. Argumenty są wartościami zwrotnymi wywołań odpowiednio do Win32 API funkcji **GetExceptionCode** i **GetExceptionInformation** .

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

W przypadku **_set_se_translator**ma wpływ na dynamiczne łączenie z CRT; inna Biblioteka DLL w procesie może wywoływać **_set_se_translator** i zamienić swój program obsługi na własny.

W przypadku korzystania z programu **_set_se_translator** z kodu zarządzanego (kod skompilowany za pomocą/CLR) lub kodu natywnego i zarządzanego, należy pamiętać, że translator wpływa na wyjątki generowane tylko w kodzie natywnym. Wszelkie zarządzane wyjątki generowane w kodzie zarządzanym (takie jak w `System::Exception`przypadku podnoszenia) nie są kierowane przez funkcję translatora. Wyjątki wywoływane w kodzie zarządzanym przy **użyciu funkcji** Win32Exception lub spowodowane przez wyjątek systemu, takie jak wyjątek dzielenia przez zero, są kierowane przez translatora.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Ten przykład otacza wywołania w celu ustawienia translatora wyjątków strukturalnych i przywrócenia starego obiektu w klasie `Scoped_SE_Translator`RAII. Ta klasa umożliwia wprowadzenie translatora specyficznego dla zakresu jako pojedynczej deklaracji. Destruktor klasy przywraca oryginalny translator, gdy kontrolka opuszcza zakres.

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
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
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

void trans_func( unsigned int u, EXCEPTION_POINTERS* )
{
    throw SE_Exception( u );
}

int main()
{
    Scoped_SE_Translator scoped_se_translator{ trans_func };
    try
    {
        SEFunc();
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught a __try exception, error %8.8x.\n", e.getSeNumber() );
    }
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Przykład

Chociaż funkcje udostępniane przez **_set_se_translator** nie są dostępne w kodzie zarządzanym, można użyć tego mapowania w kodzie natywnym, nawet jeśli ten kod natywny jest w kompilacji pod przełącznikiem **/CLR** , o ile kod natywny jest wskazane przy `#pragma unmanaged`użyciu. Jeśli wystąpi wyjątek strukturalny w kodzie zarządzanym, który ma zostać zamapowany, kod generujący i obsługujący wyjątek musi być oznaczony `#pragma unmanaged`. Poniższy kod pokazuje możliwe użycie. Aby uzyskać więcej informacji, zobacz [dyrektywy pragma i słowo kluczowe __pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <stdio.h>
#include <exception>

int thrower_func( int i ) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS )
{
    throw SE_Exception( u );
}

void DoTest()
{
    try
    {
        thrower_func( 10 );
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught SE_Exception, error %8.8x\n", e.getSeNumber() );
    }
    catch(...)
    {
        printf( "Caught unexpected SEH exception.\n" );
    }
}
#pragma managed

int main() {
    Scoped_SE_Translator scoped_se_translator{ my_trans_func };

    DoTest();
}
```

```Output
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków — procedury](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[kończyć](terminate-crt.md)<br/>
[oczekiwan](unexpected-crt.md)<br/>
