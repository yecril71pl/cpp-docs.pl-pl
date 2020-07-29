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
ms.openlocfilehash: d8c9538c9f3d889360c0527ba538e9e091df0755
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229964"
---
# <a name="compiler-options-macros"></a>Makra opcji kompilatora

Te makra sterują określonymi funkcjami kompilatora.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Symbol, który umożliwia błędy w projektach przekonwertowanych z poprzednich wersji ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Zdefiniuj, czy co najmniej jeden z obiektów ma używać wątków apartamentu.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Sprawia, że niektóre `CString` konstruktory są jawne, zapobiegając niezamierzonym konwersji.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Zdefiniuj to makro, aby użyć standardowej składni zgodnej języka C++, która generuje błąd kompilatora C4867, gdy składnia niestandardowa jest używana do inicjowania wskaźnika do funkcji członkowskiej.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Zdefiniuj, czy co najmniej jeden z obiektów ma korzystać z wątków bezpłatnych, czy neutralnych.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Symbol wskazujący, że projekt będzie miał obiekty, które są oznaczone jako zarówno, bezpłatny, jak i neutralny. Należy zamiast tego użyć makra [_ATL_FREE_THREADED](#_atl_free_threaded) .|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Symbol, który uniemożliwia domyślne użycie przestrzeni nazw jako ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Symbol uniemożliwiający kompilowanie kodu związanego z modelem COM przy użyciu projektu.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Symbol, który uniemożliwia zainicjowanie wskaźnika tabeli metod w konstruktorze i destruktorze klasy.|
|[ATL_NOINLINE](#atl_noinline)|Symbol wskazujący, że funkcja nie powinna być wbudowana.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Zdefiniuj, czy wszystkie obiekty korzystają z modelu pojedynczego wątku.|

## <a name="_atl_all_warnings"></a><a name="_atl_all_warnings"></a>_ATL_ALL_WARNINGS

Symbol, który umożliwia błędy w projektach przekonwertowanych z poprzednich wersji ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Uwagi

Przed Visual C++ .NET 2002, ATL wyłączył wiele ostrzeżeń i pozostawiono je wyłączyć, aby nigdy nie były wyświetlane w kodzie użytkownika. W szczególności:

- Wyrażenie warunkowe C4127 jest stałą

- C4786 ': identyfikator został obcięty do znaków "number" w informacjach o debugowaniu

- Użyto niestandardowego rozszerzenia C4201: pustego struct/Union

- C4103 "filename": używany #pragma Pack do zmiany wyrównania

- C4291 "Deklaracja": nie znaleziono pasującego operatora delete; pamięć nie zostanie zwolniona, jeśli Inicjalizacja zgłosi wyjątek

- C4268 "Identyfikator": "const" dane statyczne/globalne zainicjowane za pomocą konstruktora domyślnego generowanego przez kompilator wypełniają obiekt zerami

- C4702 nieosiągalny kod

W projektach przekonwertowanych z poprzednich wersji te ostrzeżenia są nadal wyłączone przez nagłówki bibliotek.

Po dodaniu następującego wiersza do pliku *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) przed dołączeniem nagłówków bibliotek można zmienić to zachowanie.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

W przypadku `#define` dodania tego elementu w nagłówkach ATL należy zachować ostrożność w celu zachowania tych ostrzeżeń, aby nie były one wyłączone globalnie (lub jeśli użytkownik jawnie wyłącza poszczególne ostrzeżenia, a nie włączy ich).

Nowe projekty mają ten `#define` zestaw w *PCH. h* (*stdafx. h* w programie Visual Studio 2017 i starszych) domyślnie.

## <a name="_atl_apartment_threaded"></a><a name="_atl_apartment_threaded"></a>_ATL_APARTMENT_THREADED

Zdefiniuj, czy co najmniej jeden z obiektów ma używać wątków apartamentu.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Uwagi

Określa wątkowość apartamentu. Aby zapoznać się z opisem modeli wątkowości dostępnych dla obiektu ATL, zobacz [Określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych opcji wątkowego i [opcji, Kreator prostych obiektów ATL](../../atl/reference/options-atl-simple-object-wizard.md) .

## <a name="_atl_cstring_explicit_constructors"></a><a name="_atl_cstring_explicit_constructors"></a>_ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Sprawia, że niektóre `CString` konstruktory są jawne, zapobiegając niezamierzonym konwersji.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Uwagi

Po zdefiniowaniu tego konstruktora wszystkie konstruktory CString, które pobierają jeden parametr, są kompilowane za pomocą słowa kluczowego Explicit, co uniemożliwia niejawne konwersje argumentów wejściowych. Oznacza to, na przykład, że jeśli _UNICODE jest zdefiniowany, jeśli spróbujesz użyć ciągu char * jako argumentu konstruktora CString, spowoduje to błąd kompilatora. Tego makra należy używać w sytuacjach, gdy trzeba zapobiec niejawnym konwersji między typami ciągów wąskich i szerokich.

Za pomocą makra _T dla wszystkich argumentów ciągu konstruktora można zdefiniować _ATL_CSTRING_EXPLICIT_CONSTRUCTORS i uniknąć błędów kompilacji, niezależnie od tego, czy _UNICODE jest zdefiniowany.

## <a name="_atl_enable_ptm_warning"></a><a name="_atl_enable_ptm_warning"></a>_ATL_ENABLE_PTM_WARNING

Zdefiniuj to makro, aby wymusić użycie standardowej składni ANSI C++ zgodnej ze wskaźnikiem do funkcji składowych. Użycie tego makra spowoduje wygenerowanie błędu kompilatora C4867, gdy niestandardowa składnia zostanie użyta do zainicjowania wskaźnika do funkcji członkowskiej.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Uwagi

Biblioteki ATL i MFC zostały zmienione tak, aby pasowały do ulepszonej standardowej zgodności języka C++ w kompilatorze Microsoft C++. Zgodnie ze standardem ANSI C++, składnia wskaźnika do funkcji składowej klasy powinna być `&CMyClass::MyFunc` .

Jeśli nie zdefiniowano [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) (przypadek domyślny), ATL/MFC wyłącza błąd C4867 w mapach makr (szczególnie w mapach komunikatów), dzięki czemu kod, który został utworzony we wcześniejszych wersjach, może nadal być gotowy do kompilacji. Jeśli zdefiniujesz **_ATL_ENABLE_PTM_WARNING**, kod powinien być zgodny ze standardem C++.

Niestandardowa forma nie jest jednak przestarzała. Należy przenieść istniejący kod do składni zgodnej ze standardem C++. Na przykład następujący kod:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Należy zmienić na:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Dla makr mapy Dodaj znak handlowego "&". Nie należy ponownie dodawać znaku w kodzie.

## <a name="_atl_free_threaded"></a><a name="_atl_free_threaded"></a>_ATL_FREE_THREADED

Zdefiniuj, czy co najmniej jeden z obiektów ma korzystać z wątków bezpłatnych, czy neutralnych.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Uwagi

Określa bezpłatną wielowątkowość. Bezpłatna wątkowość jest równoważna z modelem apartamentu wielowątkowej. Aby zapoznać się z opisem modeli wątkowości dostępnych dla obiektu ATL, zobacz [Określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych opcji wątkowego i [opcji, Kreator prostych obiektów ATL](../../atl/reference/options-atl-simple-object-wizard.md) .

## <a name="_atl_multi_threaded"></a><a name="_atl_multi_threaded"></a>_ATL_MULTI_THREADED

Symbol wskazujący, że projekt będzie miał obiekty, które są oznaczone jako zarówno, bezpłatny, jak i neutralny.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Uwagi

Jeśli ten symbol jest zdefiniowany, ATL będzie ściągać kod, który będzie poprawnie synchronizować dostęp do danych globalnych. Zamiast tego nowy kod powinien używać równoważnego makra [_ATL_FREE_THREADED](#_atl_free_threaded) .

## <a name="_atl_no_automatic_namespace"></a><a name="_atl_no_automatic_namespace"></a>_ATL_NO_AUTOMATIC_NAMESPACE

Symbol, który uniemożliwia domyślne użycie przestrzeni nazw jako ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Uwagi

Jeśli ten symbol nie jest zdefiniowany, w tym atlbase. h zostanie wykonane **przy użyciu przestrzeni nazw ATL** domyślnie, co może prowadzić do konfliktów nazw. Aby tego uniknąć, Zdefiniuj ten symbol.

## <a name="_atl_no_com_support"></a><a name="_atl_no_com_support"></a>_ATL_NO_COM_SUPPORT

Symbol uniemożliwiający kompilowanie kodu związanego z modelem COM przy użyciu projektu.

```
_ATL_NO_COM_SUPPORT
```

## <a name="atl_no_vtable"></a><a name="atl_no_vtable"></a>ATL_NO_VTABLE

Symbol, który uniemożliwia zainicjowanie wskaźnika tabeli metod w konstruktorze i destruktorze klasy.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Uwagi

Jeśli wskaźnik tablic wirtualnych nie zostanie zainicjowany w konstruktorze i destruktorze klasy, konsolidator może wyeliminować tablicę i wszystkie funkcje, do których się odwołuje. Rozwija do **`__declspec(novtable)`** .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

## <a name="atl_noinline"></a><a name="atl_noinline"></a>ATL_NOINLINE

Symbol wskazujący, że funkcja nie powinna być wbudowana.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parametry

*myFunction*<br/>
Funkcja, która nie powinna być wbudowana.

### <a name="remarks"></a>Uwagi

Użyj tego symbolu, aby upewnić się, że funkcja nie jest umieszczona w wierszu przez kompilator, mimo że musi być zadeklarowana jako wbudowana, tak aby można ją było umieścić w pliku nagłówkowym. Rozwija do **`__declspec(noinline)`** .

## <a name="_atl_single_threaded"></a><a name="_atl_single_threaded"></a>_ATL_SINGLE_THREADED

Zdefiniuj, czy wszystkie obiekty używają modelu jednowątkowego

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Uwagi

Określa, że obiekt jest zawsze uruchamiany w podstawowym wątku COM. Aby zapoznać się z opisem modeli wątkowości dostępnych dla obiektu ATL, zobacz [Określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych opcji wątkowego i [opcji, Kreator prostych obiektów ATL](../../atl/reference/options-atl-simple-object-wizard.md) .

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)
