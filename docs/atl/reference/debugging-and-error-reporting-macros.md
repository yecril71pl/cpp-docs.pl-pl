---
title: Debugowanie i raportowanie błędów makra
ms.date: 05/06/2019
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
ms.openlocfilehash: 69ab6e17bfb1ec85ddb5b8c19c18010a9b4f3df6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330187"
---
# <a name="debugging-and-error-reporting-macros"></a>Debugowanie i raportowanie błędów makra

Te makra zapewniają przydatne debugowanie i śledzenie obiektów.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Zapisuje w oknie danych wyjściowych wszelkie przecieki `_Module.Term` interfejsu, które są wykrywane po wywołaniu.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Zapisuje wszystkie `QueryInterface` wywołania do okna danych wyjściowych.|
|[ATLASSERT](#atlassert)|Wykonuje tę samą funkcjonalność, co [makro _ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) znalezione w bibliotece czasu wykonywania języka C.|
|[ATLENSURE ( ATLENSURE )](#atlensure)|Wykonuje sprawdzanie poprawności parametrów. W `AtlThrow` razie potrzeby zadzwoń|
|[ATLTRACENOTIMPL (ATLTRACENOTIMPL)](#atltracenotimpl)|Wysyła komunikat do urządzenia zrzutu, że określona funkcja nie jest zaimplementowana.|
|[ATLTRACE ( ATLTRACE )](#atltrace)|Zgłasza ostrzeżenia do urządzenia wyjściowego, takiego jak okno debugera, zgodnie ze wskazanymi flagami i poziomami. Dołączone do zgodności z powrotem.|
|[ATLTRACE2 (ATLTRACE2)](#atltrace2)|Zgłasza ostrzeżenia do urządzenia wyjściowego, takiego jak okno debugera, zgodnie ze wskazanymi flagami i poziomami.|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES

Zdefiniuj to makro przed dołączeniem plików nagłówkowych ATL do śledzenia wszystkich `AddRef` i `Release` wywołuje interfejsy składników do okna wyjściowego.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Uwagi

Dane wyjściowe śledzenia będą wyświetlane w sposób pokazany poniżej:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

Pierwszą częścią każdego śledzenia `ATL: QIThunk`zawsze będzie . Dalej jest wartość identyfikującą określonego *interfejsu thunk* używane. Thunk interfejsu jest obiektem używanym do obsługi liczby odwołań i zapewnić możliwości śledzenia używane w tym miejscu. Nowy interfejs thunk jest tworzony `QueryInterface` przy każdym wywołaniu, z wyjątkiem żądań dla `IUnknown` interfejsu (w tym przypadku ten sam thunk jest zwracany za każdym razem, aby były zgodne z regułami tożsamości COM).

Następnie zobaczysz `AddRef` lub `Release` wskaż, która metoda została wywołana. Następnie zostanie wyświetlone wartości identyfikujące obiekt, którego liczba odwołań do interfejsu została zmieniona. Wartość śledzona jest **ten** wskaźnik obiektu.

Liczba odwołań, która jest śledzona jest `AddRef` liczba `Release` odwołań na tym thunk po lub został wywołany. Należy zauważyć, że ta liczba odwołań może nie odpowiadać liczbie odwołań dla obiektu. Każdy thunk zachowuje własną liczbę odwołań, aby pomóc Ci w pełni przestrzegać reguł liczenia odwołań COM.

Ostatnią informacją śledzone jest nazwa obiektu i interfejsu, którego `AddRef` dotyczy `Release` lub wywołania.

Wszelkie przecieki interfejsu, które są wykrywane, `_Module.Term` gdy serwer zostanie zamknięty i jest wywoływana będą rejestrowane w ten sposób:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

Informacje podane w tym miejscu mapuje bezpośrednio do informacji podanych w poprzednich instrukcji śledzenia, dzięki czemu można zbadać liczby odwołań przez cały okres istnienia thunk interfejsu. Ponadto można uzyskać wskazanie maksymalnej liczby odwołań na tym interfejsie thunk.

> [!NOTE]
> _ATL_DEBUG_INTERFACES mogą być używane w kompilacjach detalicznych.

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI

Zapisuje wszystkie `QueryInterface` wywołania do okna danych wyjściowych.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Uwagi

Jeśli wywołanie `QueryInterface` nie powiodło się, w oknie wyjściowym zostaną wyświetlone:

*nazwa interfejsu* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a>ATLASSERT

Makro ATLASSERT pełni tę samą funkcjonalność, co makro [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) znalezione w bibliotece czasu wykonywania języka C.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Parametry

*booleanWyrażenie*<br/>
Wyrażenie (w tym wskaźniki), które ma wartość niezerowa lub 0.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania atlassert ocenia *booleanExpression* i generuje raport debugowania, gdy wynik jest false.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldef.h

## <a name="atlensure"></a><a name="atlensure"></a>ATLENSURE ( ATLENSURE )

To makro służy do sprawdzania poprawności parametrów przekazanych do funkcji.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Parametry

*booleanWyrażenie*<br/>
Określa wyrażenie logiczne, które ma zostać przetestowane.

*Hr*<br/>
Określa kod błędu do zwrócenia.

### <a name="remarks"></a>Uwagi

Te makra zapewniają mechanizm wykrywania i powiadamiania użytkownika o nieprawidłowym użyciu parametrów.

Makro wywołuje atlassert, a jeśli `AtlThrow`warunek nie powiedzie się, wywoła .

W przypadku ATLENSURE, `AtlThrow` jest wywoływana z E_FAIL.

W ATLENSURE_THROW przypadku `AtlThrow` jest wywoływana z określonym HRESULT.

Różnica między ATLENSURE i ATLASSERT jest, że ATLENSURE zgłasza wyjątek w kompilacjach release, a także w debug kompilacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL (ATLTRACENOTIMPL)

W kompilacjach debugowania ATL wysyła ciąg *"funcname* nie jest zaimplementowany" do urządzenia zrzutu i zwraca E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Parametry

*funcname (nazwa zabawy)*<br/>
[w] Ciąg zawierający nazwę funkcji, która nie jest zaimplementowana.

### <a name="remarks"></a>Uwagi

W kompilacjach wydania po prostu zwraca E_NOTIMPL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltrace.h

## <a name="atltrace"></a><a name="atltrace"></a>ATLTRACE ( ATLTRACE )

Zgłasza ostrzeżenia do urządzenia wyjściowego, takiego jak okno debugera, zgodnie ze wskazanymi flagami i poziomami. Dołączone do zgodności z powrotem.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Parametry

*Exp*<br/>
[w] Ciąg i zmienne do wysłania do okna danych wyjściowych lub dowolnej aplikacji, która zalewkowuje te komunikaty.

*Kategorii*<br/>
[w] Typ zdarzenia lub metody, na której ma być raportowana. Zobacz Uwagi, aby uzyskać listę kategorii.

*Poziom*<br/>
[w] Poziom śledzenia raportu. Zobacz uwagi, aby uzyskać szczegółowe informacje.

*lpszFormat*<br/>
[w] Sformatowany ciąg do wysłania do urządzenia zrzutu.

### <a name="remarks"></a>Uwagi

Opis [ATLTRACEE](#atltrace2) można znaleźć w opisie ATLTRACE. ATLTRACE i ATLTRACE2 mają takie samo zachowanie, ATLTRACE jest dołączony do zgodności z powrotem.

## <a name="atltrace2"></a><a name="atltrace2"></a>ATLTRACE2 (ATLTRACE2)

Zgłasza ostrzeżenia do urządzenia wyjściowego, takiego jak okno debugera, zgodnie ze wskazanymi flagami i poziomami.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>Parametry

*Exp*<br/>
[w] Ciąg do wysłania do okna danych wyjściowych lub dowolnej aplikacji, która zalewkowuje te komunikaty.

*Kategorii*<br/>
[w] Typ zdarzenia lub metody, na której ma być raportowana. Zobacz Uwagi, aby uzyskać listę kategorii.

*Poziom*<br/>
[w] Poziom śledzenia raportu. Zobacz uwagi, aby uzyskać szczegółowe informacje.

*lpszFormat*<br/>
[w] Ciąg `printf`formatu stylu używany do tworzenia ciągu do wysłania do urządzenia zrzutu.

### <a name="remarks"></a>Uwagi

Krótka forma ATLTRACE2 zapisuje ciąg do okna wyjściowego debugera. Druga forma ATLTRACE2 zapisuje również dane wyjściowe w oknie wyjściowym debugera, ale podlega ustawieniom narzędzia śledzenia ATL/MFC (patrz [przykład ATLTraceTool](../../overview/visual-cpp-samples.md)). Na przykład jeśli ustawisz *poziom* 4 i ATL/MFC Trace Tool na poziomie 0, nie zobaczysz komunikatu. *może* to być 0, 1, 2, 3 lub 4. Domyślnie 0 zgłasza tylko najpoważniejsze problemy.

Parametr *kategorii* zawiera listę flag śledzenia do ustawionego. Flagi te odpowiadają typom metod, dla których chcesz zgłosić. Poniższe tabele wyświetlają prawidłowe flagi śledzenia, których można użyć dla parametru *kategorii.*

### <a name="atl-trace-flags"></a>Flagi śledzenia ATL

|Kategoria ATL|Opis|
|------------------|-----------------|
|`atlTraceGeneral`|Raporty dotyczące wszystkich aplikacji ATL. Domyślnie.|
|`atlTraceCOM`|Raporty na temat metod COM.|
|`atlTraceQI`|Raporty dotyczące wywołań QueryInterface.|
|`atlTraceRegistrar`|Raporty dotyczące rejestracji obiektów.|
|`atlTraceRefcount`|Raporty dotyczące zmiany liczby odwołań.|
|`atlTraceWindowing`|Raporty dotyczące metod systemu Windows; na przykład zgłasza nieprawidłowy identyfikator mapy wiadomości.|
|`atlTraceControls`|Sprawozdania z kontroli; na przykład raporty, gdy formant lub jego okno jest niszczone.|
|`atlTraceHosting`|Raporty hosting wiadomości; na przykład raporty, gdy klient w kontenerze jest aktywowany.|
|`atlTraceDBClient`|Raporty dotyczące szablonu konsumenta OLE DB; na przykład, gdy wywołanie GetData nie powiedzie się, dane wyjściowe mogą zawierać HRESULT.|
|`atlTraceDBProvider`|Raporty dotyczące szablonu dostawcy ole db; na przykład raporty, jeśli utworzenie kolumny nie powiodło się.|
|`atlTraceSnapin`|Raporty dla aplikacji MmC SnapIn.|
|`atlTraceNotImpl`|Raporty, że wskazana funkcja nie jest zaimplementowana.|
|`atlTraceAllocation`|Raporty wiadomości drukowane przez narzędzia do debugowania pamięci w atldbgmem.h.|

### <a name="mfc-trace-flags"></a>Flagi śledzenia MFC

|Kategoria MFC|Opis|
|------------------|-----------------|
|`traceAppMsg`|Ogólnego przeznaczenia, komunikaty MFC. Zawsze zalecane.|
|`traceDumpContext`|Wiadomości z [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Wiadomości z kodu obsługi wiadomości MFC.|
|`traceMemory`|Komunikaty z kodu zarządzania pamięcią MFC.|
|`traceCmdRouting`|Wiadomości z kodu routingu polecenia MFC systemu Windows.|
|`traceHtml`|Komunikaty z obsługi okna dialogowego DHTML MFC.|
|`traceSocket`|Komunikaty z obsługi gniazda MFC.|
|`traceOle`|Wiadomości z obsługi OLE MFC.|
|`traceDatabase`|Wiadomości z obsługi bazy danych MFC.|
|`traceInternet`|Wiadomości z pomocy technicznej MFC w Internecie.|

Aby zadeklarować niestandardową kategorię śledzenia, `CTraceCategory` należy zadeklarować globalne wystąpienie klasy w następujący sposób:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

Nazwa kategorii, MY_CATEGORY w tym przykładzie, jest nazwą określoną dla parametru *kategorii.* Pierwszym parametrem jest nazwa kategorii, która pojawi się w narzędziu śledzenia ATL/MFC. Drugi parametr jest domyślnym poziomem śledzenia. Ten parametr jest opcjonalny, a domyślny poziom śledzenia wynosi 0.

Aby użyć kategorii zdefiniowanej przez użytkownika:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Aby określić, że chcesz filtrować komunikaty śledzenia, wstaw definicje tych `#include <atlbase.h>` makr do pliku Stdafx.h przed instrukcją.

Alternatywnie można ustawić filtr w dyrektywach preprocesora w oknie dialogowym **Strony właściwości.** Kliknij kartę **Preprocesor,** a następnie wstaw globalną do pola edycji **Definicje preprocesora.**

Atlbase.h zawiera domyślne definicje makr ATLTRACE2 i te definicje będą używane, jeśli nie zdefiniujesz tych symboli przed przetworzeniem atlbase.h.

W kompilacjach wersji ATLTRACE2 `(void) 0`kompiluje się do .

ATLTRACE2 ogranicza zawartość ciągu, który ma zostać wysłany do urządzenia zrzutu, do nie więcej niż 1023 znaków, po formatowaniu.

ATLTRACE i ATLTRACE2 mają takie samo zachowanie, ATLTRACE jest dołączony do zgodności z powrotem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)<br/>
[Debugowanie i raportowanie błędów funkcje globalne](../../atl/reference/debugging-and-error-reporting-global-functions.md)
