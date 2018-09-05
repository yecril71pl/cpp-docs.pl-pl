---
title: Makra debugowania i raportowania błędów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
dev_langs:
- C++
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef417232d62c664b4943a2198ae351a5c443b089
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763750"
---
# <a name="debugging-and-error-reporting-macros"></a>Makra debugowania i raportowania błędów

Te makra udostępniać przydatne narzędzia do debugowania i śledzenia.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Zapisuje w oknie danych wyjściowych przecieków dowolny interfejs, który po wykryciu `_Module.Term` jest wywoływana.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Zapisuje wszystkie wywołania do `QueryInterface` w oknie danych wyjściowych.|
|[ATLASSERT](#atlassert)|Wykonuje te same funkcje co [_asserte —](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) — makro dostępnych w bibliotece wykonawczej C.|
|[ATLENSURE](#atlensure)|Sprawdza poprawność parametrów. Wywołaj `AtlThrow` w razie potrzeby|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Wysyła komunikat do urządzenia zrzutu określona funkcja nie jest zaimplementowana.|
|[ATLTRACE](#alttrace)|Raporty ostrzeżenia na urządzeniach, takich jak okna debugera, zgodnie z wskazany flagami i poziomów. Dostępny dla zgodności z poprzednimi wersjami.|
|[ATLTRACE2](#atltrace2)|Raporty ostrzeżenia na urządzeniach, takich jak okna debugera, zgodnie z wskazany flagami i poziomów.|

##  <a name="_atl_debug_interfaces"></a>  _ATL_DEBUG_INTERFACES

Zdefiniuj to makro, przed dołączeniem żadnych plików nagłówkowych ATL., aby śledzić wszystkie `AddRef` i `Release` wywołuje przez interfejsy składników usługi w oknie danych wyjściowych.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Uwagi

Dane wyjściowe śledzenia będą wyświetlane, jak pokazano poniżej:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

Pierwsza część każdego śledzenia będą zawsze `ATL: QIThunk`. Następnym ekranem jest zidentyfikowanie określonych wartości *interfejsu thunk* używane. Thunk interfejsu jest obiekt służący do utrzymywania licznika odwołań i zapewnia możliwość śledzenia, używany w tym miejscu. Nowe thunk interfejs jest tworzony na każde wywołanie `QueryInterface` z wyjątkiem żądań dotyczących `IUnknown` interfejsu (w tym przypadku samej thunk jest zwracana zawsze do są zgodne z regułami tożsamości modelu COM).

Następnie zobaczysz `AddRef` lub `Release` wskazujący, która metoda została wywołana. Poniżej zobaczysz wartość identyfikuje obiekt, którego licznik odwołań interfejs został zmieniony. Wartość śledzone **to** wskaźnika obiektu.

Licznik odwołań, który jest śledzony jest licznik odwołań w tym thunk po `AddRef` lub `Release` została wywołana. Należy zwrócić uwagę na to, czy ten licznik odwołań może nie być zgodna licznik odwołań dla obiektu. Każdy thunk zachowuje swój własny licznika odwołań i pomóc w pełni zgodne z regułami liczenie odwołań w modelu COM.

Ostatni etap informacji śledzone jest nazwą obiektu oraz interfejs wpływowi `AddRef` lub `Release` wywołania.

Dowolny interfejs przecieków, które są wykrywane podczas wyłączania serwera i `_Module.Term` nosi nazwę będą rejestrowane następująco:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

Informacje przedstawione tutaj mapuje bezpośrednio do informacji podanych w poprzednich instrukcji śledzenia, dzięki czemu można sprawdzić liczby odwołań, w okresie istnienia całego thunk interfejsu. Ponadto możesz uzyskać wskazanie maksymalną liczbę odwołań na wywołanie tego interfejsu.

> [!NOTE]
> _ATL_DEBUG_INTERFACES może służyć w sprzedaży detalicznej.

##  <a name="_atl_debug_qi"></a>  _ATL_DEBUG_QI

Zapisuje wszystkie wywołania do `QueryInterface` w oknie danych wyjściowych.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Uwagi

Jeśli wywołanie `QueryInterface` nie powiodło się, w oknie dane wyjściowe będą wyświetlane:

*Nazwa interfejsu* - `failed`

##  <a name="atlassert"></a>  ATLASSERT

Makra ATLASSERT wykonuje te same funkcje co [_asserte —](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) — makro dostępnych w bibliotece wykonawczej C.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Parametry

*booleanExpression*  
Wyrażenie (w tym wskaźniki), zwraca wartość różną od zera lub równa 0.

### <a name="remarks"></a>Uwagi

W przypadku kompilacji do debugowania, ocenia ATLASSERT *booleanExpression* i generuje raport debugowania, jeśli wynik to false.  

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldef.h

##  <a name="atlensure"></a>  ATLENSURE

To makro jest używane do sprawdzania poprawności parametrów przekazanych do funkcji.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Parametry

*booleanExpression*  
Określa wyrażenie logiczne do zbadania.

*godz.*  
Określa kod błędu do zwrócenia.

### <a name="remarks"></a>Uwagi

Te makra udostępniają mechanizm wykrywania i powiadamia użytkownika o użycie nieprawidłowy parametr.

Makro wywołuje ATLASSERT i jeśli warunek zakończy się niepowodzeniem wywołania `AtlThrow`.

W przypadku ATLENSURE `AtlThrow` jest wywoływana z E_FAIL.

W przypadku ATLENSURE_THROW `AtlThrow` jest wywoływana z określonym elementem HRESULT.

Różnica między ATLENSURE i ATLASSERT polega na tym, że ATLENSURE zgłasza wyjątek w kompilacjach wydania, jak również tak jak w przypadku kompilacji do debugowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h  

##  <a name="atltracenotimpl"></a>  ATLTRACENOTIMPL

W kompilacjach do debugowania ATL wysyła ciąg " *funcname* nie jest zaimplementowana" na urządzeniu zrzutu i zwraca E_NOTIMPL.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Parametry

*funcname*  
[in] Ciąg zawierający nazwę funkcji, która nie jest zaimplementowana.

### <a name="remarks"></a>Uwagi

W kompilacjach wydania należy po prostu zwraca E_NOTIMPL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Wymagania

**Nagłówek:** atltrace.h 

##  <a name="atltrace"></a>  ATLTRACE

Raporty ostrzeżenia na urządzeniach, takich jak okna debugera, zgodnie z wskazany flagami i poziomów. Dostępny dla zgodności z poprzednimi wersjami.

```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Parametry

*EXP*  
[in] Parametry i zmienne, aby wysyłać w oknie danych wyjściowych programu Visual C++ lub inna aplikacja te komunikaty pułapek.

*category*  
[in] Typ zdarzenia lub metody, na którym do raportu. Zobacz uwagi, aby uzyskać listę kategorii.

*poziom*  
[in] Poziom śledzenia do raportu. Zobacz uwagi, aby uzyskać szczegółowe informacje.

*lpszFormat*  
[in] Sformatowany ciąg, aby wysłać do urządzenia zrzutu.

### <a name="remarks"></a>Uwagi

Zobacz [ATLTRACE2](#atltrace2) opis ATLTRACE. ATLTRACE i ATLTRACE2 mają takie samo zachowanie, ATLTRACE jest włączone dla zachowania zgodności z poprzednimi wersjami.

##  <a name="atltrace2"></a>  ATLTRACE2

Raporty ostrzeżenia na urządzeniach, takich jak okna debugera, zgodnie z wskazany flagami i poziomów.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```

### <a name="parameters"></a>Parametry

*EXP*  
[in] Ciąg do wysyłania do okna danych wyjściowych Visual C++ lub dowolnej aplikacji, która te komunikaty pułapek.

*category*  
[in] Typ zdarzenia lub metody, na którym do raportu. Zobacz uwagi, aby uzyskać listę kategorii.

*poziom*  
[in] Poziom śledzenia do raportu. Zobacz uwagi, aby uzyskać szczegółowe informacje.

*lpszFormat*  
[in] `printf`— Styl ciągu formatu służące do tworzenia ciągu, aby wysłać do urządzenia zrzutu.

### <a name="remarks"></a>Uwagi

Krótkiej formy ATLTRACE2 zapisuje ciąg w oknie danych wyjściowych debugera. Druga forma ATLTRACE2 również zapisuje dane wyjściowe do okna danych wyjściowych debugera, ale jest zgodnie z ustawieniami narzędzie śledzenia ATL/MFC (zobacz [przykładowe ATLTraceTool](../../visual-cpp-samples.md)). Na przykład jeśli ustawisz *poziom* 4. i narzędzie śledzenia ATL/MFC do poziomu 0, nie zostanie wyświetlony komunikat. *poziom* może być 0, 1, 2, 3 lub 4. Wartość domyślna 0, raporty najpoważniejszych problemów.

*Kategorii* parametru wyświetla listę flag śledzenia, aby ustawić. Te flagi odnoszą się do typów, metod, dla których chcesz sporządzić raport. W poniższych tabelach flagi śledzenia prawidłowy, można użyć dla *kategorii* parametru.

### <a name="atl-trace-flags"></a>Flagi śledzenia ATL

|Kategoria ATL|Opis|
|------------------|-----------------|
|`atlTraceGeneral`|Raporty dotyczące wszystkich aplikacji ATL. Domyślnie.|
|`atlTraceCOM`|Raporty dotyczące metod COM.|
|`atlTraceQI`|Raporty w wywołaniach funkcji QueryInterface.|
|`atlTraceRegistrar`|Raporty dotyczące rejestracji obiektów.|
|`atlTraceRefcount`|Raporty o zmienianiu licznika odwołań.|
|`atlTraceWindowing`|Raporty dotyczące metod systemu windows; na przykład raporty nieprawidłowy identyfikator komunikatu mapy.|
|`atlTraceControls`|Raporty dotyczące kontroli; na przykład raportów, kiedy niszczony jest formantu lub jego okna.|
|`atlTraceHosting`|Raporty obsługi wiadomości. na przykład raporty po aktywowaniu klienta w kontenerze.|
|`atlTraceDBClient`|Raporty dotyczące OLE DB konsumenta szablonu. na przykład gdy wywołanie metody GetData kończy się niepowodzeniem, danych wyjściowych może zawierać HRESULT.|
|`atlTraceDBProvider`|Raporty dotyczące OLE DB Provider szablonu. na przykład raporty, jeśli nie można utworzyć kolumny.|
|`atlTraceSnapin`|Raporty dotyczące aplikacji przystawka programu MMC.|
|`atlTraceNotImpl`|Raporty o wskazanym funkcja nie jest zaimplementowana.|
|`atlTraceAllocation`|Raporty drukowanymi przez ilość pamięci, narzędzia debugowania w atldbgmem.h wiadomości.|

### <a name="mfc-trace-flags"></a>Flagi śledzenia MFC

|Kategoria MFC|Opis|
|------------------|-----------------|
|`traceAppMsg`|Ogólnego przeznaczenia, komunikatów MFC. Zawsze jest to zalecane.|
|`traceDumpContext`|Komunikaty z [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Komunikaty z kodu MFC komunikatów.|
|`traceMemory`|Komunikaty z kod zarządzania pamięci biblioteki MFC.|
|`traceCmdRouting`|Komunikaty z Windows MFC polecenia rozliczeniowy.|
|`traceHtml`|Komunikaty z obsługi okna dialogowego DHTML MFC.|
|`traceSocket`|Komunikaty z obsługi gniazda MFC.|
|`traceOle`|Komunikaty z obsługi OLE MFC.|
|`traceDatabase`|Komunikaty z obsługi bazy danych MFC.|
|`traceInternet`|Komunikaty z obsługi Internet MFC.|

Aby zadeklarować kategorii niestandardowe śledzenia, należy zadeklarować globalnego wystąpienia `CTraceCategory` klasy w następujący sposób:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

Nazwa kategorii, MY_CATEGORY w tym przykładzie jest nazwa służąca do *kategorii* parametru. Pierwszy parametr jest nazwa kategorii, która będzie wyświetlana w narzędzie śledzenia ATL/MFC. Drugi parametr jest domyślny poziom śledzenia. Ten parametr jest opcjonalny, a domyślny poziom śledzenia ma wartość 0.

Aby użyć kategorii zdefiniowanych przez użytkownika:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Aby określić, czy filtrowanie komunikatów śledzenia, należy wstawić definicji dla tych makr do Stdafx.h przed `#include <atlbase.h>` instrukcji.

Alternatywnie możesz ustawić filtr w dyrektywy preprocesora w **stron właściwości** okno dialogowe. Kliknij przycisk **preprocesora** kartę, a następnie wstawianie globalne do **definicje preprocesora** pole edycji.

Atlbase.h zawiera domyślne definicje makr ATLTRACE2 i definicje te zostaną użyte, jeśli przed przetworzeniem atlbase.h nie zdefiniujesz te symbole.

W kompilacjach do wydania ATLTRACE2 kompiluje, aby `(void) 0`.

ATLTRACE2 ogranicza zawartość ciągu do wysłania do urządzenia zrzutu do nie więcej niż 1023 znaków po sformatowaniu.

ATLTRACE i ATLTRACE2 mają takie samo zachowanie, ATLTRACE jest włączone dla zachowania zgodności z poprzednimi wersjami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra](../../atl/reference/atl-macros.md)   
[Funkcje globalne debugowania i raportowania błędów](../../atl/reference/debugging-and-error-reporting-global-functions.md)
