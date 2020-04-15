---
title: Makra opcji kompilatora
ms.date: 08/19/2019
f1_keywords:
- _ATL_ALL_WARNINGS
- _ATL_APARTMENT_THREADED
- '_ATL_CSTRING_EXPLICIT_CONSTRUCTORS '
- _ATL_ENABLE_PTM_WARNING
- _ATL_FREE_THREADED
- _ATL_MULTI_THREADED
- _ATL_NO_AUTOMATIC_NAMESPACE
- _ATL_NO_COM_SUPPORT
- ATL_NO_VTABLE
- ATL_NOINLINE
- _ATL_SINGLE_THREADED
helpviewer_keywords:
- compiler options, macros
ms.assetid: a869adc6-b3de-4299-b040-9ae20b45f82c
ms.openlocfilehash: 702324c3300ff23bb60113529a681e3b8fa99354
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331621"
---
# <a name="compiler-options-macros"></a>Makra opcji kompilatora

Te makra kontrolują określone funkcje kompilatora.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Symbol, który włącza błędy w projektach konwertowanych z poprzednich wersji ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Zdefiniuj, czy jeden lub więcej obiektów używa wątków mieszkania.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Sprawia, `CString` że niektóre konstruktory jawne, zapobiegając niezamierzone konwersje.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Zdefiniuj to makro w celu użycia składni zgodnej ze standardem C++, która generuje błąd kompilatora C4867, gdy niestandardowa składnia jest używana do inicjowania wskaźnika do funkcji elementu członkowskiego.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Zdefiniuj, czy jeden lub więcej obiektów używa wątków wolnych lub neutralnych.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Symbol wskazujący projekt będzie miał obiekty, które są oznaczone jako zarówno, wolne lub neutralne. Zamiast tego należy użyć [_ATL_FREE_THREADED](#_atl_free_threaded) makr.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Symbol, który uniemożliwia domyślne użycie przestrzeni nazw jako ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Symbol, który uniemożliwia kompilowanie kodu związanego z com z projektem.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Symbol, który uniemożliwia vtable wskaźnik inicjuje w konstruktorze klasy i destruktora.|
|[ATL_NOINLINE](#atl_noinline)|Symbol wskazujący funkcję nie powinien być inlined.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Zdefiniuj, czy wszystkie obiekty używają modelu pojedynczego wątku.|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

Symbol, który włącza błędy w projektach konwertowanych z poprzednich wersji ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Uwagi

Przed Visual C++ .NET 2002 ATL wyłączone wiele ostrzeżeń i pozostawił je wyłączone, tak aby nigdy nie pojawił się w kodzie użytkownika. Są to:

- Wyrażenie warunkowe C4127 jest stałe

- C4786 "identyfikator": identyfikator został obcięty do znaków "numer" w informacjach debugowania

- Używane niestandardowe rozszerzenie C4201 : bezimienna struktura/unia

- C4103 'nazwa pliku': używany #pragma pack do zmiany wyrównania

- C4291 "deklaracja": nie znaleziono usuwania pasującego operatora; pamięć nie zostanie zwolniona, jeśli inicjalizacja zda wyjątek

- C4268 "identyfikator" : "const" statyczne/globalne dane zainicjowane za pomocą wygenerowanego przez kompilatora domyślnego konstruktora wypełnia obiekt zerami

- C4702 nieosiągalny kod

W projektach przekonwertowanych z poprzednich wersji te ostrzeżenia są nadal wyłączone przez nagłówki bibliotek.

Dodając następujący wiersz do pliku *pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych) przed dołączeniem nagłówków bibliotek, to zachowanie można zmienić.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Jeśli `#define` zostanie to dodane, nagłówki ATL są ostrożne, aby zachować stan tych ostrzeżeń, tak aby nie są wyłączone globalnie (lub jeśli użytkownik jawnie wyłącza poszczególne ostrzeżenia, aby nie włączyć je).

Nowe projekty `#define` mają ten zestaw w *pch.h* (*stdafx.h* w programie Visual Studio 2017 i wcześniejszych) domyślnie.

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

Zdefiniuj, czy jeden lub więcej obiektów używa wątków mieszkania.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Uwagi

Określa wątki apartamentu. Zobacz [Określanie modelu wątkowego projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych opcji wątków i [opcje, Kreator obiektów prostych ATL](../../atl/reference/options-atl-simple-object-wizard.md) opis modeli wątków dostępnych dla obiektu ATL.

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Sprawia, `CString` że niektóre konstruktory jawne, zapobiegając niezamierzone konwersje.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Uwagi

Gdy ten konstruktor jest zdefiniowany, wszystkie konstruktory CString, które przyjmują pojedynczy parametr są kompilowane za pomocą jawnego słowa kluczowego, co zapobiega niejawnym konwersjom argumentów wejściowych. Oznacza to, na przykład, że po zdefiniowaniu _UNICODE, jeśli spróbujesz użyć ciągu char* jako argument konstruktora CString, spowoduje to błąd kompilatora. Użyj tego makra w sytuacjach, w których należy zapobiegać konwersjom niejawnym między typami ciągów wąskich i szerokich.

Za pomocą makra _T na wszystkich argumentów ciągu konstruktora, można zdefiniować _ATL_CSTRING_EXPLICIT_CONSTRUCTORS i uniknąć błędów kompilacji, niezależnie od tego, czy _UNICODE jest zdefiniowany.

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

Zdefiniuj to makro, aby wymusić użycie standardowej składni zgodnej ze standardem ANSI C++ dla funkcji wskaźnika do elementów członkowskich. Użycie tego makra spowoduje, że błąd kompilatora C4867 zostanie wygenerowany, gdy niestandardowa składnia jest używana do inicjowania wskaźnika do funkcji elementu członkowskiego.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Uwagi

Biblioteki ATL i MFC zostały zmienione, aby były zgodne z ulepszoną standardową zgodnością kompilatora Języka C++ firmy Microsoft. Zgodnie ze standardem ANSI C++ składnia wskaźnika do funkcji `&CMyClass::MyFunc`elementu członkowskiego klasy powinna być .

Gdy [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) nie jest zdefiniowany (przypadek domyślny), ATL/MFC wyłącza błąd C4867 w mapach makr (zwłaszcza mapy wiadomości), dzięki czemu kod, który został utworzony we wcześniejszych wersjach, może nadal tworzyć jak poprzednio. Jeśli zdefiniujesz **_ATL_ENABLE_PTM_WARNING,** kod powinien być zgodny ze standardem C++.

Jednak niestandardowy formularz został przestarzały. Należy przenieść istniejący kod do standardowej składni zgodnej ze standardem C++. Na przykład następujący kod:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Należy zmienić na:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

W przypadku makr mapy dodaj znak ampersand "&". Nie należy ponownie dodawać znaku w kodzie.

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

Zdefiniuj, czy jeden lub więcej obiektów używa wątków wolnych lub neutralnych.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Uwagi

Określa wolne wątki. Swobodne gwintowanie jest równoznaczne z modelem mieszkania wielowątkowe. Zobacz [Określanie modelu wątkowego projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych opcji wątków i [opcje, Kreator obiektów prostych ATL](../../atl/reference/options-atl-simple-object-wizard.md) opis modeli wątków dostępnych dla obiektu ATL.

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

Symbol wskazujący projekt będzie miał obiekty, które są oznaczone jako zarówno, wolne lub neutralne.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Uwagi

Jeśli ten symbol jest zdefiniowany, ATL będzie pobierać kod, który będzie poprawnie synchronizować dostęp do danych globalnych. Nowy kod powinien zamiast tego używać równoważnego [_ATL_FREE_THREADED](#_atl_free_threaded) makra.

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

Symbol, który uniemożliwia domyślne użycie przestrzeni nazw jako ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Uwagi

Jeśli ten symbol nie jest zdefiniowany, w tym atlbase.h będzie działać **przy użyciu przestrzeni nazw ATL** domyślnie, co może prowadzić do konfliktów nazewnictwa. Aby temu zapobiec, zdefiniuj ten symbol.

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

Symbol, który uniemożliwia kompilowanie kodu związanego z com z projektem.

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a>ATL_NO_VTABLE

Symbol, który uniemożliwia vtable wskaźnik inicjuje w konstruktorze klasy i destruktora.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Uwagi

Jeśli wskaźnik vtable nie jest inicjowany w konstruktorze klasy i destruktora, konsolidator można wyeliminować vtable i wszystkie funkcje, do których wskazuje. Rozwija się do **__declspec(novtable)**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a>ATL_NOINLINE

Symbol wskazujący funkcję nie powinien być inlined.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parametry

*myfunction (myfunction)*<br/>
Funkcja, która nie powinna być inlined.

### <a name="remarks"></a>Uwagi

Użyj tego symbolu, jeśli chcesz upewnić się, że funkcja nie zostanie inlined przez kompilator, nawet jeśli musi być zadeklarowany jako wbudowany, tak aby można było umieścić w pliku nagłówka. Rozwija się do **__declspec(noinline)**.

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

Zdefiniuj, czy wszystkie obiekty używają modelu pojedynczego wątku

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Uwagi

Określa, że obiekt jest zawsze uruchamiany w podstawowym wątku COM. Zobacz [Określanie modelu wątkowego projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych opcji wątków i [opcje, Kreator obiektów prostych ATL](../../atl/reference/options-atl-simple-object-wizard.md) opis modeli wątków dostępnych dla obiektu ATL.

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)
