---
title: Makra opcji kompilatora
ms.date: 11/04/2016
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
ms.openlocfilehash: 79b1cabc0304e905012db5f6dd73ed71073c0c1e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258479"
---
# <a name="compiler-options-macros"></a>Makra opcji kompilatora

Te makra kontrolowania kompilatora określonych funkcji.

|||
|-|-|
|[_ATL_ALL_WARNINGS](#_atl_all_warnings)|Symbol, który umożliwia błędy w projektach konwertowany z poprzednich wersji ATL.|
|[_ATL_APARTMENT_THREADED](#_atl_apartment_threaded)|Zdefiniuj użycie co najmniej jeden z obiektów wątkowości typu apartment.|
|[_ATL_CSTRING_EXPLICIT_CONSTRUCTORS](#_atl_cstring_explicit_constructors)|Sprawia, że niektóre `CString` konstruktory jawne uniemożliwić wszystkie konwersje niezamierzone.|
|[_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning)|Zdefiniuj to makro, aby można było używać składni języka C++ standard zgodne, który generuje błąd kompilatora C4867, gdy używana jest inny niż standardowy składnia w celu zainicjowania wskaźnika do funkcji członkowskiej.|
|[_ATL_FREE_THREADED](#_atl_free_threaded)|Zdefiniuj użycie co najmniej jeden z obiektów bezpłatnej lub neutralnym wątków.|
|[_ATL_MULTI_THREADED](#_atl_multi_threaded)|Symbol, który wskazuje, projekt będzie miał obiektów, które są oznaczone jako zarówno w warstwie bezpłatna lub neutralna. Makro [_ATL_FREE_THREADED](#_atl_free_threaded) powinny być używane zamiast tego.|
|[_ATL_NO_AUTOMATIC_NAMESPACE](#_atl_no_automatic_namespace)|Symbol, co uniemożliwia używanie domyślnej przestrzeni nazw jako ATL.|
|[_ATL_NO_COM_SUPPORT](#_atl_no_com_support)|Symbol, który uniemożliwia związane z COM kod kompilowany z projektem.|
|[ATL_NO_VTABLE](#atl_no_vtable)|Symbol, który uniemożliwia inicjowanego w Konstruktor i destruktor klasy wskaźnika vtable.|
|[ATL_NOINLINE](#atl_noinline)|Symbol, który wskazuje funkcji nie może być śródwierszowa.|
|[_ATL_SINGLE_THREADED](#_atl_single_threaded)|Określenie, czy wszystkie obiekty używać pojedynczego modelu wątkowości.|

##  <a name="_atl_all_warnings"></a>  _ATL_ALL_WARNINGS

Symbol, który umożliwia błędy w projektach konwertowany z poprzednich wersji ATL.

```
#define _ATL_ALL_WARNINGS
```

### <a name="remarks"></a>Uwagi

Przed Visual C++ .NET 2002 ATL wyłączone wiele ostrzeżeń i pozostawić je wyłączyć, aby ich nigdy nie pojawiło się w kodzie użytkownika. W szczególności:

- C4127 wyrażenie warunkowe jest stałą

- C4786 'Identyfikator': identyfikator został obcięty do 'Liczba' znaków w informacjach debugowania

- C4201 użyto niestandardowego rozszerzenia: typ struct/union

- C4103 'NazwaPliku': #pragma pack umożliwia zmienianie wyrównania

- C4291 "deklaracją": nie pasującego operatora delete odnaleziony; pamięć nie zostanie zwolniona, jeśli Inicjalizacja generuje wyjątek

- C4268 'Identyfikator': "const" statyczne/globalne dane zainicjowano przy użyciu wygenerowanego przez kompilator domyślnego konstruktora, który wypełnił obiekt zerami

- C4702 nieosiągalnego kodu

W projektach konwertowany z poprzednich wersji tych ostrzeżeń są nadal wyłączone przez nagłówki bibliotek.

Dodając następujący wiersz w pliku stdafx.h przed dołączeniem bibliotek, nagłówków, można zmienić to zachowanie.

[!code-cpp[NVC_ATL_Utilities#97](../../atl/codesnippet/cpp/compiler-options-macros_1.h)]

Jeśli ten `#define` dodaniu nagłówki ATL są uważać, aby zachować stan tych ostrzeżeń, tak, aby nie są globalnie wyłączone (lub użytkownik jawnie wyłącza wyświetlanie ostrzeżeń indywidualnych, nie w celu umożliwienia im).

Nowe projekty mają to `#define` domyślnie ustawione w pliku stdafx.h.

##  <a name="_atl_apartment_threaded"></a>  _ATL_APARTMENT_THREADED

Zdefiniuj użycie co najmniej jeden z obiektów wątkowości typu apartment.

```
_ATL_APARTMENT_THREADED
```

### <a name="remarks"></a>Uwagi

Określa wątkowości typu apartment. Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych wątków opcje, a [opcji, Kreator obiektów proste ATL](../../atl/reference/options-atl-simple-object-wizard.md) opis wątkowości modele dostępne dla obiektu ATL.

##  <a name="_atl_cstring_explicit_constructors"></a>  _ATL_CSTRING_EXPLICIT_CONSTRUCTORS

Sprawia, że niektóre `CString` konstruktory jawne uniemożliwić wszystkie konwersje niezamierzone.

```
_ATL_CSTRING_EXPLICIT_CONSTRUCTORS
```

### <a name="remarks"></a>Uwagi

Jeśli to jest zdefiniowana, wszystkie konstruktory CString przyjmujące jeden parametr są kompilowane z jawnym słowem kluczowym, co uniemożliwia niejawne konwersje argumentów wejściowych. Oznacza to, na przykład, że gdy _UNICODE zdefiniowano, jeśli próba użycia char * ciągu jako argument konstruktora obiektu CString i powoduje błąd kompilatora. Użyj tego makra w sytuacjach wymagających zapobiec niejawnej konwersji między typami wąskich, jak i szerokich.

Za pomocą makra _T na wszystkie argumenty typu string konstruktora, można zdefiniować _ATL_CSTRING_EXPLICIT_CONSTRUCTORS i uniknąć błędów kompilacji, niezależnie od tego, czy _UNICODE zdefiniowano.

##  <a name="_atl_enable_ptm_warning"></a>  _ATL_ENABLE_PTM_WARNING

Zdefiniuj to makro, aby wymusić użycie składni CLS standard ANSI C++ dla wskaźnika do funkcji Członkowskich. Użycie tego makra spowoduje błąd kompilatora C4867 wygenerowany, gdy używana jest składnia niestandardowych w celu zainicjowania wskaźnika do funkcji członkowskiej.

```
#define _ATL_ENABLE_PTM_WARNING
```

### <a name="remarks"></a>Uwagi

Aby dopasować udoskonalone standardowe zgodności C++ kompilator języka Visual C++ zostały zmienione biblioteki ATL i MFC. Zgodnie ze standardem ANSI w języku C++, składnia wskaźnika do funkcji składowej klasy powinna mieć `&CMyClass::MyFunc`.

Gdy [_ATL_ENABLE_PTM_WARNING](#_atl_enable_ptm_warning) nie zdefiniowano (przypadek domyślny) ATL/MFC wyłącza błąd C4867 w społeczności maps — makro (mapy wiadomości przede wszystkim) tak, aby kod, który został utworzony we wcześniejszych wersjach mogą w dalszym ciągu kompilacji, tak jak poprzednio. Jeśli zdefiniujesz **_ATL_ENABLE_PTM_WARNING**, kod powinien być standard C++ zgodne.

Jednak niestandardowych formularza jest przestarzała, więc należy przenieść istniejący kod do standardowej składni zgodny z języka C++. Na przykład poniższy kod:

[!code-cpp[NVC_MFCListView#14](../../atl/reference/codesnippet/cpp/compiler-options-macros_2.cpp)]

Należy je zmienić:

[!code-cpp[NVC_MFCListView#11](../../atl/reference/codesnippet/cpp/compiler-options-macros_3.cpp)]

Należy pamiętać, że dla makra mapy dodających znaku "&", nie należy dodawać go ponownie w kodzie.

##  <a name="_atl_free_threaded"></a>  _ATL_FREE_THREADED

Zdefiniuj użycie co najmniej jeden z obiektów bezpłatnej lub neutralnym wątków.

```
_ATL_FREE_THREADED
```

### <a name="remarks"></a>Uwagi

Określa, wolnych wątków. Wolnych wątków jest równoważna z modelem apartamentu wielowątkowych. Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych wątków opcje, a [opcji, Kreator obiektów proste ATL](../../atl/reference/options-atl-simple-object-wizard.md) opis wątkowości modele dostępne dla obiektu ATL.

##  <a name="_atl_multi_threaded"></a>  _ATL_MULTI_THREADED

Symbol, który wskazuje, projekt będzie miał obiektów, które są oznaczone jako zarówno w warstwie bezpłatna lub neutralna.

```
_ATL_MULTI_THREADED
```

### <a name="remarks"></a>Uwagi

Jeśli ten symbol jest zdefiniowany, ATL będzie pobierać w kodzie, który będzie poprawnie synchronizować dostęp do danych globalnych. Nowy kod powinien używać równoważnej — makro [_ATL_FREE_THREADED](#_atl_free_threaded) zamiast tego.

##  <a name="_atl_no_automatic_namespace"></a>  _ATL_NO_AUTOMATIC_NAMESPACE

Symbol, co uniemożliwia używanie domyślnej przestrzeni nazw jako ATL.

```
_ATL_NO_AUTOMATIC_NAMESPACE
```

### <a name="remarks"></a>Uwagi

Jeśli ten symbol nie jest zdefiniowany, w tym atlbase.h wykona **za pomocą przestrzeni nazw ATL** domyślnie, co może prowadzić do konfliktów nazw. Aby tego uniknąć, należy zdefiniować tego symbolu.

##  <a name="_atl_no_com_support"></a>  _ATL_NO_COM_SUPPORT

Symbol, który uniemożliwia związane z COM kod kompilowany z projektem.

```
_ATL_NO_COM_SUPPORT
```

##  <a name="atl_no_vtable"></a>  ATL_NO_VTABLE

Symbol, który uniemożliwia inicjowanego w Konstruktor i destruktor klasy wskaźnika vtable.

```
ATL_NO_VTABLE
```

### <a name="remarks"></a>Uwagi

Jeśli inicjowanego w klasie Konstruktor i destruktor nie może wskaźnik vtable, konsolidator wyeliminować vtable i wszystkie funkcje, które wskazuje. Rozwija **__declspec(novtable)**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_COM#53](../../atl/codesnippet/cpp/compiler-options-macros_4.h)]

##  <a name="atl_noinline"></a>  ATL_NOINLINE

Symbol, który wskazuje funkcji nie może być śródwierszowa.

```
    ATL_NOINLINE inline
    myfunction()
    {
    ...
    }
```

### <a name="parameters"></a>Parametry

*myfunction*<br/>
Funkcja, która nie może być śródwierszowa.

### <a name="remarks"></a>Uwagi

Jeśli chcesz upewnić się, że funkcja nie uzyska śródwierszowych przez kompilator, mimo że musi być zadeklarowana jako wbudowaną, dzięki czemu można je umieścić w pliku nagłówkowym, należy użyć tego symbolu. Rozwija **__declspec(noinline)**.

##  <a name="_atl_single_threaded"></a>  _ATL_SINGLE_THREADED

Umożliwia określenie, czy wszystkie obiekty używać pojedynczego modelu wątkowości

```
_ATL_SINGLE_THREADED
```

### <a name="remarks"></a>Uwagi

Określa, czy obiekt jest zawsze uruchamiany w podstawowym wątku com. Zobacz [określanie modelu wątkowości projektu](../../atl/specifying-the-threading-model-for-a-project-atl.md) dla innych wątków opcje, a [opcji, Kreator obiektów proste ATL](../../atl/reference/options-atl-simple-object-wizard.md) opis wątkowości modele dostępne dla obiektu ATL.

## <a name="see-also"></a>Zobacz także

[Makra](../../atl/reference/atl-macros.md)
