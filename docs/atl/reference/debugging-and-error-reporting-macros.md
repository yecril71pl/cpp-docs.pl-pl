---
title: "Makra debugowania i raportowanie błędów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9098b944f70ab4e4448fe40aa2347b0128e6e1a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-error-reporting-macros"></a>Makra debugowania i raportowanie błędów
Te makra udostępniać przydatne narzędzia debugowania i śledzenia.  
  
|||  
|-|-|  
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Zapisuje w oknie danych wyjściowych przecieków każdy interfejs, który po wykryciu `_Module.Term` jest wywoływana.|  
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Zapisuje wszystkie wywołania `QueryInterface` w oknie danych wyjściowych.|  
|[ATLASSERT](#atlassert)|Wykonuje te same funkcje co [_asserte —](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makro znaleziono biblioteki wykonawcze języka C.|  
|[ATLENSURE](#atlensure)|Sprawdza poprawność parametrów. Wywołanie `AtlThrow` w razie potrzeby|  
|[ATLTRACENOTIMPL](#atltracenotimpl)|Wysyła komunikat do urządzenia zrzutu określona funkcja nie jest zaimplementowana.|  
|[ATLTRACE](#alttrace)|Raporty ostrzeżenia na urządzeniach, takich jak okna debugera, zgodnie z określoną flagi i poziomów. Zawarte dla zgodności z poprzednimi wersjami.|  
|[ATLTRACE2](#atltrace2)|Raporty ostrzeżenia na urządzeniach, takich jak okna debugera, zgodnie z określoną flagi i poziomów.|  
  
##  <a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES  
 Zdefiniuj to makro przed dołączeniem wszelkie pliki nagłówkowe ATL do śledzenia wszystkich `AddRef` i **wersji** wywołuje dla interfejsów składników programu w oknie danych wyjściowych.  
  
```
#define _ATL_DEBUG_INTERFACES
```  
  
### <a name="remarks"></a>Uwagi  
 Dane wyjściowe śledzenia będą wyświetlane, jak pokazano poniżej:  
  
 `ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`  
  
 Pierwsza część każdego śledzenia będzie zawsze `ATL: QIThunk`. Następnie jest wartością identyfikowania danej *interfejsu thunk* używany. Thunk interfejsu jest obiekt służący do utrzymywania liczebności referencyjnej i możliwości śledzenia używane w tym miejscu. Nowe thunk interfejsu jest tworzony przy każdym wywołaniu do `QueryInterface` z wyjątkiem żądań **IUnknown** interfejsu (w tym przypadku samej thunk jest zwracany zawsze przestrzegania zasad tożsamości modelu COM).  
  
 Następnie zostanie wyświetlony `AddRef` lub **wersji** wskazujący, która metoda została wywołana. Następujące, zostanie wyświetlona wartość identyfikowania obiektów, których liczba odwołań interfejs został zmieniony. Wartość śledzone jest **to** wskaźnika obiektu.  
  
 Liczba odwołań, śledzonego jest liczba odwołań w tym thunk po `AddRef` lub **wersji** została wywołana. Należy pamiętać, ten licznik odwołania nie zgadzają liczba odwołań dla obiekt. Każdy thunk zachowuje własną liczba odwołań, aby pomóc w pełni zgodne z zasadami liczenie odwołań w modelu COM.  
  
 Ostatni element informacji śledzona jest nazwą obiektu i interfejsu wpływowi `AddRef` lub **wersji** wywołania.  
  
 Żadnego interfejsu przecieki, które są wykrywane podczas zamykania serwera i `_Module.Term` jest nazywany będą rejestrowane następująco:  
  
 `ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`  
  
 Informacje podane w tym miejscu map bezpośrednio do informacji dostępnych w poprzednich instrukcji śledzenia, tak, można sprawdzić odwołanie zlicza w okresie istnienia całego thunk interfejsu. Ponadto możesz uzyskać wskazuje maksymalną liczbę odwołań na thunk tego interfejsu.  
  
> [!NOTE]
> `_ATL_DEBUG_INTERFACES`można w sprzedaży detalicznej kompilacji.  
  
##  <a name="_atl_debug_qi"></a>_ATL_DEBUG_QI  
 Zapisuje wszystkie wywołania `QueryInterface` w oknie danych wyjściowych.  
  
```
#define _ATL_DEBUG_QI
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wywołanie `QueryInterface` nie powiodło się, w oknie dane wyjściowe będą wyświetlane:  
  
 *Nazwa interfejsu* - `failed`  
  
##  <a name="atlassert"></a>ATLASSERT  
 `ATLASSERT` Makro wykonuje te same funkcje co [_asserte —](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) makro znaleziono biblioteki wykonawcze języka C.  
  
```
ATLASSERT(booleanExpression);
```  
  
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Wyrażenie (w tym wskaźników), którego wynikiem jest różna od zera lub równa 0.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach do debugowania `ATLASSERT` ocenia `booleanExpression` i generuje raport debugowania, gdy wynik ma wartość false.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldef.h  
    
##  <a name="atlensure"></a>ATLENSURE  
 To makro jest używane do sprawdzania poprawności parametrów przekazanych do funkcji.  
  
```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```  
  
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Określa wyrażenie warunkowe do sprawdzenia.  
  
 `hr`  
 Określa kod błędu do zwrócenia.  
  
### <a name="remarks"></a>Uwagi  
 Te makra udostępniają mechanizm wykrywania i powiadamia użytkownika o użycie nieprawidłowy parametr.  
  
 Wywołania makro `ATLASSERT` i jeśli warunek nie powiedzie się wywołania `AtlThrow`.  
  
 W **ATLENSURE** przypadku `AtlThrow` jest wywoływana z E_FAIL.  
  
 W **ATLENSURE_THROW** przypadku `AtlThrow` jest wywoływana z określonym HRESULT.  
  
 Różnica między **ATLENSURE** i `ATLASSERT` jest to, że **ATLENSURE** zgłasza wyjątek w wersji tworzy także w kompilacjach debugowania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  

##  <a name="atltracenotimpl"></a>ATLTRACENOTIMPL  
 W kompilacjach do debugowania ATL wysyła ciąg " `funcname` nie jest zaimplementowana" zrzutu urządzenia i zwraca **E_NOTIMPL**.  
  
```
ATLTRACENOTIMPL(funcname);
```  
  
### <a name="parameters"></a>Parametry  
 `funcname`  
 [in] Ciąg zawierający nazwę funkcji, która nie jest zaimplementowana.  
  
### <a name="remarks"></a>Uwagi  
 W kompilacjach wydania, po prostu zwraca **E_NOTIMPL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atltrace.h 

##  <a name="atltrace"></a>ATLTRACE
 Raporty ostrzeżenia na urządzeniach, takich jak okna debugera, zgodnie z określoną flagi i poziomów. Zawarte dla zgodności z poprzednimi wersjami.  
  
```
ATLTRACE(exp);

ATLTRACE(  
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```  
  
### <a name="parameters"></a>Parametry  
 `exp`  
 [in] Parametry i zmienne do wysłania w oknie danych wyjściowych programu Visual C++ lub dowolnej aplikacji, która traps te komunikaty.  
  
 `category`  
 [in] Typ zdarzenia lub metody, na którym do raportu. Zobacz uwagi dla listy kategorii.  
  
 `level`  
 [in] Poziom śledzenia do raportu. Zobacz uwagi, aby uzyskać szczegółowe informacje.  
  
 `lpszFormat`  
 [in] Sformatowany ciąg do wysłania do urządzenia zrzutu.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [ATLTRACE2](#atltrace2) opis **ATLTRACE**. **ATLTRACE** i `ATLTRACE2` ma takie samo zachowanie **ATLTRACE** dla zgodności z poprzednimi wersjami.  
  
##  <a name="atltrace2"></a>ATLTRACE2  
 Raporty ostrzeżenia na urządzeniach, takich jak okna debugera, zgodnie z określoną flagi i poziomów.  
  
```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTRlpszFormat,  ...);
```  
  
### <a name="parameters"></a>Parametry  
 `exp`  
 [in] Ciąg do wysłania w oknie danych wyjściowych programu Visual C++ lub dowolnej aplikacji, która traps tych wiadomości.  
  
 `category`  
 [in] Typ zdarzenia lub metody, na którym do raportu. Zobacz uwagi dla listy kategorii.  
  
 `level`  
 [in] Poziom śledzenia do raportu. Zobacz uwagi, aby uzyskać szczegółowe informacje.  
  
 `lpszFormat`  
 [in] `printf`-Ciągu formatu na potrzeby tworzenia ciągu do wysłania do urządzenia zrzutu.  
  
### <a name="remarks"></a>Uwagi  
 Krótka forma z `ATLTRACE2` zapisuje ciąg do debugera do okna wyjściowego. Drugiej formy `ATLTRACE2` również zapisuje dane wyjściowe w oknie danych wyjściowych debugera, ale jest zgodnie z ustawieniami narzędzie śledzenia ATL/MFC (zobacz [próbki ATLTraceTool](../../visual-cpp-samples.md)). Na przykład jeśli ustawisz `level` 4 i narzędzie śledzenia ATL/MFC do poziomu 0, nie zostanie wyświetlony komunikat. *poziom* może być 0, 1, 2, 3 lub 4. Wartość domyślna 0, raporty najpoważniejszych problemów.  
  
 `category` Flagi śledzenia, aby ustawić zawiera listę parametrów. Te flagi odpowiadają typy metod, dla których chcesz zgłosić. Poniższe tabele zawierają listę flagi śledzenia prawidłowy, można użyć dla `category` parametru.  
  
### <a name="atl-trace-flags"></a>Flagi śledzenia ATL  
  
|Kategoria ATL|Opis|  
|------------------|-----------------|  
|`atlTraceGeneral`|Raporty dotyczące wszystkich aplikacji ATL. Domyślnie.|  
|`atlTraceCOM`|Raporty dotyczące metod COM.|  
|`atlTraceQI`|Raporty na wywołania metody QueryInterface.|  
|`atlTraceRegistrar`|Raporty dotyczące rejestracji obiektów.|  
|`atlTraceRefcount`|Raporty dotyczące zmiany liczba odwołań.|  
|`atlTraceWindowing`|Raporty dotyczące systemu windows metody; na przykład raporty nieprawidłowy identyfikator komunikatu mapy.|  
|`atlTraceControls`|Raporty dotyczące kontroli; na przykład informuje, kiedy formantu lub jego okno zostanie zniszczone.|  
|`atlTraceHosting`|Raporty dotyczące obsługi wiadomości. na przykład raporty po aktywowaniu klienta w kontenerze.|  
|`atlTraceDBClient`|Raporty dotyczące OLE DB szablon konsumenta; na przykład po wywołaniu metody GetData kończy się niepowodzeniem, danych wyjściowych może zawierać HRESULT.|  
|`atlTraceDBProvider`|Raporty dotyczące OLE DB Provider szablonu. na przykład raporty, jeśli nie można utworzyć kolumny.|  
|`atlTraceSnapin`|Raporty dotyczące aplikacji konsoli MMC.|  
|`atlTraceNotImpl`|Raporty wskazanych funkcja nie jest zaimplementowana.|  
|**atlTraceAllocation**|Zgłasza komunikaty drukowanymi przez narzędzia debugowania w atldbgmem.h pamięci.|  
  
### <a name="mfc-trace-flags"></a>Flagi śledzenia MFC  
  
|Kategoria MFC|Opis|  
|------------------|-----------------|  
|**traceAppMsg**|Ogólnego przeznaczenia, komunikatów MFC. Zawsze zalecane.|  
|**traceDumpContext**|Komunikaty z [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|  
|**traceWinMsg**|Komunikaty z kod obsługi komunikatów MFC.|  
|**traceMemory**|Komunikaty z MFC pamięci zarządzania kodu.|  
|**traceCmdRouting**|Komunikaty z systemu Windows w MFC polecenie rozliczeniowy.|  
|**traceHtml**|Komunikaty z MFC DHTML okno obsługi.|  
|**traceSocket**|Komunikaty z obsługi gniazda MFC.|  
|**traceOle**|Komunikaty z Obsługa OLE MFC.|  
|**traceDatabase**|Komunikaty z obsługa baz danych MFC.|  
|**traceInternet**|Obsługuje komunikaty z Internetu MFC.|  
  
 Aby zadeklarować kategorii śledzenia niestandardowych, Zadeklaruj globalne wystąpienie `CTraceCategory` klas w następujący sposób:  
  
 [!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]  
  
 Nazwa kategorii `MY_CATEGORY` w tym przykładzie jest nazwa nadana do `category` parametru. Pierwszym parametrem jest nazwa kategorii, która będzie wyświetlana w narzędzie śledzenia ATL/MFC. Drugi parametr jest domyślny poziom śledzenia. Ten parametr jest opcjonalny, a domyślny poziom śledzenia jest równa 0.  
  
 Aby użyć kategorii zdefiniowanej przez użytkownika:  
  
 [!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]  
  
 Aby określić, że chcesz filtrować komunikaty śledzenia, włóż definicje makr do Stdafx.h przed `#include <atlbase.h>` instrukcji.  
  
 Można również ustawić filtr w dyrektywy preprocesora w **strony właściwości** okno dialogowe. Kliknij przycisk **preprocesora** karcie, a następnie wstawianie globalne do **definicje preprocesora** polu edycji.  
  
 Atlbase.h zawiera definicje domyślne `ATLTRACE2` makra i definicje te zostaną użyte, jeśli nie Definiuj symbole przed przetworzeniem atlbase.h.  
  
 W kompilacjach wydania `ATLTRACE2` kompiluje do `(void) 0`.  
  
 `ATLTRACE2`ogranicza zawartość ciąg, który ma zostać wysłany do urządzeń zrzutu do nie więcej niż 1023 znaków po sformatowaniu.  
  
 **ATLTRACE** i `ATLTRACE2` ma takie samo zachowanie **ATLTRACE** dla zgodności z poprzednimi wersjami.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra](../../atl/reference/atl-macros.md)   
 [Funkcje globalne debugowania i raportowania błędów](../../atl/reference/debugging-and-error-reporting-global-functions.md)
