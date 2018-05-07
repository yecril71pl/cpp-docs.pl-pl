---
title: Usługi diagnostyczne | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- diagnosi [MFC]s, diagnostic services
- diagnostic macros [MFC], list of general MFC
- services [MFC], diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables [MFC]
- diagnostics [MFC], diagnostic functions and variables
- diagnostics [MFC], list of general MFC
- diagnosis [MFC], diagnostic functions and variables
- diagnosis [MFC], list of general MFC
- general diagnostic macros in MFC
- diagnostic macros [MFC]
- diagnostic services [MFC]
- object diagnostic functions in MFC
- diagnostics [MFC], diagnostic services
- diagnostic functions and variables [MFC]
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2332090032a93152b6c841336538bf9d45984300
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="diagnostic-services"></a>Usługi diagnostyczne
Microsoft Foundation Class Library udostępnia wiele usług diagnostycznych, które debugowanie programów łatwiejsze. Usługi diagnostyczne te obejmują makra i funkcje globalne, które umożliwiają śledzenie pamięci programu alokacji, zrzutu zawartość obiektów w czasie wykonywania i Drukuj komunikaty debugowania w czasie wykonywania. Makra i funkcje globalne dla usługi diagnostyczne są podzielone na następujące kategorie:  
  
-   Ogólne makra diagnostyczne  
  
-   Ogólne funkcje diagnostyczne i zmienne  
  
-   Funkcje diagnostyczne obiektów  
  
 Te makra i funkcje są dostępne dla wszystkich klas pochodnych `CObject` w wersjach Debug i Release MFC. Jednak wszystkie z wyjątkiem `DEBUG_NEW` i **Sprawdź** nic nie rób w wersji.  
  
 W bibliotece debugowania wszystkie bloki alokacji pamięci jest oddzielona z serii "guard bajtów." Jeśli zakłóceń w przez zapisu pamięci wadliwe tych bajtów procedury diagnostycznych może zgłosić problem. Jeśli dołączysz wiersz:  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 w pliku implementacji wszystkich wywołań **nowe** zapisze filename i numer wiersza których alokacji pamięci miała miejsce. Funkcja [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) wyświetli te informacje dodatkowe, umożliwiając zidentyfikować przecieki pamięci. Odnoszą się również do klasy [CDumpContext](../../mfc/reference/cdumpcontext-class.md) dodatkowe informacje na temat diagnostycznych danych wyjściowych.  
  
 Ponadto biblioteki wykonawczej języka C obsługuje również zestaw funkcji diagnostycznych używanego do debugowania aplikacji. Aby uzyskać więcej informacji, zobacz [debugować procedury](../../c-runtime-library/debug-routines.md) w odwołaniu biblioteki czasu wykonywania.  
  
### <a name="mfc-general-diagnostic-macros"></a>Makra diagnostyczne ogólne MFC  
  
|||  
|-|-|  
|[ASSERT](#assert)|Drukuje wiadomość, a następnie przerywa program, jeśli wynikiem obliczenia określonego wyrażenia jest **FALSE** w wersji do debugowania biblioteki.|  
|[ASSERT_KINDOF —](#assert_kindof)|Testy, które obiekt jest obiektem określonej klasy lub klasę pochodzącą od określonej klasy.|  
|[ASSERT_VALID —](#assert_valid)|Testy wewnętrzne ważności obiektu przez wywołanie jego `AssertValid` funkcji członkowskiej; zazwyczaj przesłoniętych z `CObject`.|
|[DEBUG_NEW —](#debug_new)|Określa nazwę pliku i numer wiersza dla obiekt Alokacja w trybie debugowania do znajdowania przecieki pamięci.|  
|[DEBUG_ONLY —](#debug_only)|Podobnie jak **ASSERT** , ale nie sprawdza wartość wyrażenia; przydatne w przypadku kodu, które mają być wykonywane tylko w trybie debugowania.|  
|[Upewnij się, że i ENSURE_VALID](#ensure)|Służy do sprawdzania poprawności danych.|
|[THIS_FILE —](#this_file)|Rozwija do nazwy pliku, który jest kompilowany.|
|[ŚLEDZENIA](#trace)|Udostępnia `printf`— takich jak funkcja w wersji do debugowania biblioteki.|  
|[SPRAWDŹ](#verify)|Podobnie jak **ASSERT** , ale oblicza wyrażenie w wersji biblioteki, a także w wersji do debugowania.|  
  
### <a name="mfc-general-diagnostic-variables-and-functions"></a>Zmienne Diagnostyka ogólne MFC i funkcje  
  
|||  
|-|-|  
|[afxdump —](#afxdump)|Zmiennej globalnej, która wysyła [CDumpContext](../../mfc/reference/cdumpcontext-class.md) informacji w oknie danych wyjściowych debugera lub terminal debugowania.|  
|[afxmemdf —](#afxmemdf)|Zmienna globalna kontrolujące zachowanie debugowanie alokatora pamięci.|  
|[Afxcheckerror —](#afxcheckerror)|Zmienna globalna wykorzystywane do testowania przekazany **SCODE** czy on jest błędem i, jeśli tak, zgłasza błąd odpowiednie.|  
|[Afxcheckmemory —](#afxcheckmemory)|Sprawdza, czy integralność wszystkich aktualnie przydzielonej pamięci.|  
|[AfxDebugBreak](#afxdebugbreak)|Powoduje przerwanie wykonywania.|
|[Afxdump —](#cdumpcontext_in_mfc)|Jeśli wywoływana, gdy w debugerze, zrzuty stan obiektu podczas debugowania.|  
|[Afxdump —](#afxdump)|Wewnętrzna funkcja zrzuty stan obiektu podczas debugowania.|
|[Afxdumpstack —](#afxdumpstack)|Generowanie obrazu bieżącego stosu. Ta funkcja jest zawsze połączone statycznie.|  
|[Afxenablememoryleakdump —](#afxenablememoryleakdump)|Włącza zrzut przeciek pamięci.|  
|[Afxenablememorytracking —](#afxenablememorytracking)|Włącza pamięć śledzenia włączać i wyłączać.|  
|[Afxismemoryblock —](#afxismemoryblock)|Sprawdza, czy poprawnie przydzielony blok pamięci.|  
|[Afxisvalidaddress —](#afxisvalidaddress)|Weryfikuje, czy w ramach programu granice zakresu adresów pamięci.|  
|[Afxisvalidstring —](#afxisvalidstring)|Określa, czy wskaźnik do ciągu jest prawidłowy.|  
|[Afxsetallochook —](#afxsetallochook)|Umożliwia wywoływanie funkcji w każdej alokacji pamięci.|  
  
### <a name="mfc-object-diagnostic-functions"></a>Funkcje diagnostyczne obiektów MFC  
  
|||  
|-|-|  
|[Afxdoforallclasses —](#afxdoforallclasses)|Wykonuje funkcję we wszystkich `CObject`-pochodnych klas, które obsługują sprawdzanie typu run-time.|  
|[Afxdoforallobjects —](#afxdoforallobjects)|Wykonuje funkcję we wszystkich `CObject`-pochodnych obiektów przydzielonych za pomocą **nowe**.|  

### <a name="mfc-compilation-macros"></a>Makra kompilacji MFC
|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Pomija ostrzeżenia kompilatora przestarzałe funkcje MFC do użytku.|  


## <a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS
Pomija ostrzeżenia kompilatora przestarzałe funkcje MFC do użytku.  
   
### <a name="syntax"></a>Składnia   
```  
_AFX_SECURE_NO_WARNINGS  
```     
### <a name="example"></a>Przykład  
 Jeśli _AFX_SECURE_NO_WARNINGS nie zostały zdefiniowane w tym przykładowym kodzie spowoduje, że ostrzeżenie kompilatora.  
  
 ```cpp
// define this before including any afx files in stdafx.h
#define _AFX_SECURE_NO_WARNINGS
```
```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a> Afxdebugbreak —
Wywołanie tej funkcji, aby spowodować przerwanie (w lokalizacji wywołanie `AfxDebugBreak`) podczas wykonywania wersja do debugowania aplikacji MFC.  

### <a name="syntax"></a>Składnia    
```
void AfxDebugBreak( );    
```  
   
### <a name="remarks"></a>Uwagi  
 `AfxDebugBreak` nie przynosi efektów w wersji aplikacji MFC i powinna zostać usunięta. Tej funkcji należy używać tylko w aplikacjach MFC. Użyj wersji interfejsu API Win32 **debugbreak —**, aby spowodować przerwy w aplikacjach innego typu niż MFC.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxver_.h   

##  <a name="assert"></a>  ASSERT
 Oblicza jej argument.  
  
```   
ASSERT(booleanExpression)   
```  
  
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Określa wyrażenie (w tym wartości wskaźnika), którego wynikiem jest różna od zera lub równa 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wynik wynosi 0, makra drukuje komunikatów diagnostycznych i przerywa ten program. Jeśli warunek nie jest różna od zera, go nie działa.  
  
 Komunikat diagnostycznych ma formularza  
  
 `assertion failed in file <name> in line <num>`  
  
 gdzie *nazwa* to nazwa pliku źródłowego i *num* jest numer wiersza to potwierdzenie, że nie powiodło się w pliku źródłowym.  
  
 W wydanej wersji programu MFC **ASSERT** nie może oszacować wyrażenia i w związku z tym nie spowoduje to przerwania programu. Jeśli można obliczyć wyrażenia, niezależnie od tego, środowisko, użyj **Sprawdź** makro zamiast **ASSERT**.  
  
> [!NOTE]
>  Ta funkcja jest dostępna tylko w wersji do debugowania MFC.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="assert_kindof"></a>  ASSERT_KINDOF —  
 To makro potwierdza, że obiekt wskazywany jest określonej klasy lub jest obiekt klasę pochodną określonej klasy.  
  
```   
ASSERT_KINDOF(classname, pobject)  
```  
  
### <a name="parameters"></a>Parametry  
 *ClassName*  
 Nazwa `CObject`-klasy.  
  
 *pobject*  
 Wskaźnik do obiektu klasy.  
  
### <a name="remarks"></a>Uwagi  
 *Pobject* parametr powinien być wskaźnik do obiektu i może być **const**. Obiekt wskazywał i klasa musi obsługiwać `CObject` informacje o klasie czasu wykonywania. Na przykład aby upewnić się, że `pDocument` wskaźnik do obiektu `CMyDoc` klasy lub dowolny z jego pochodne można kodu:  
  
 [!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]  
  
 Przy użyciu `ASSERT_KINDOF` makro jest dokładnie taka sama jak kodowanie:  
  
 [!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]  
  
 Ta funkcja działa tylko w przypadku klasy zadeklarowany z [declare_dynamic —] (declare_dynamic — # Uruchom — czas obiektu — model-services.md lub [declare_serial —](run-time-object-model-services.md#declare_serial) makra.  
  
> [!NOTE]
>  Ta funkcja jest dostępna tylko w wersji do debugowania MFC.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="assert_valid"></a>  ASSERT_VALID —  
 Służy do testowania założeń dotyczących ważności stanu wewnętrznego obiektu.  
  
```   
ASSERT_VALID(pObject)   
```  
  
### <a name="parameters"></a>Parametry  
 `pObject`  
 Określa obiekt klasy pochodzącej od `CObject` mający zastępowanie wersji `AssertValid` funkcję elementu członkowskiego.  
  
### <a name="remarks"></a>Uwagi  
 `ASSERT_VALID` wywołania `AssertValid` funkcji członkowskiej obiektu przekazany jako jej argument.  
  
 W wydanej wersji programu MFC `ASSERT_VALID` nie działają. W wersji do debugowania, sprawdza poprawność wskaźnika, sprawdza przed **NULL**i wywołuje metodę obiektu własnych `AssertValid` funkcji elementów członkowskich. Jeśli którakolwiek z tych testów kończy się niepowodzeniem, zostanie wyświetlony komunikat alertu w taki sam sposób jak [ASSERT](#assert).  
  
> [!NOTE]
>  Ta funkcja jest dostępna tylko w wersji do debugowania MFC.  
  
 Aby uzyskać dodatkowe informacje i przykłady, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW —  
 Ułatwia wyszukiwanie przecieków pamięci.  
  
```   
#define  new DEBUG_NEW   
```  
  
### <a name="remarks"></a>Uwagi  
 Można użyć `DEBUG_NEW` wszędzie w programie, zwykle za pomocą którego **nowe** operatora, aby przydzielić magazyn stosu.  
  
 W trybie debugowania (gdy **_DEBUG** symbol jest zdefiniowana), `DEBUG_NEW` przechowuje informacje o nazwę i numer wiersza dla każdego obiektu, który go przydziela. Następnie, jeśli używasz [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) funkcji członkowskiej poszczególnych obiektów przydzielonych za pomocą `DEBUG_NEW` jest wyświetlany numer pliku, a wiersz gdzie została przydzielona.  
  
 Aby użyć `DEBUG_NEW`, Wstaw następujące dyrektywy do plików źródłowych:  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 Po wstawieniu tej dyrektywy preprocesora powoduje wstawienie `DEBUG_NEW` wszędzie tam, gdzie można użyć **nowe**, a reszta MFC. Podczas kompilowania wydanej wersji programu, `DEBUG_NEW` jest rozpoznawana jako prosty **nowe** operacji i informacje pliku, a wiersz nie zostały wygenerowane.  
  
> [!NOTE]
>  W poprzednich wersjach MFC (4.1 i starszych) niezbędną do `#define` instrukcji po wszystkich instrukcji, które wywołuje `IMPLEMENT_DYNCREATE` lub `IMPLEMENT_SERIAL` makra. To nie jest już konieczne.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY —  
 W trybie debugowania (gdy **_DEBUG** symbol jest zdefiniowana), `DEBUG_ONLY` ocenia jej argument.  
  
```   
DEBUG_ONLY(expression)   
```  
  
### <a name="remarks"></a>Uwagi  
 W kompilacji wydania **debug_only —** nie może oszacować jej argument. Jest to przydatne, gdy masz kod, które mają zostać wykonane tylko w przypadku kompilacji do debugowania.  
  
 `DEBUG_ONLY` Makro jest odpowiednikiem otaczającego *wyrażenie* z **#ifdef _DEBUG** i `#endif`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h

 ### <a name="ensure"></a>  Upewnij się, że i ENSURE_VALID
Służy do sprawdzania poprawności danych.  
   
### <a name="syntax"></a>Składnia    
```
ENSURE(  booleanExpression )  
ENSURE_VALID( booleanExpression  )  
```
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Określa wyrażenie warunkowe do sprawdzenia.  
   
### <a name="remarks"></a>Uwagi  
 Celem tych makr jest zwiększające sprawdzanie poprawności parametrów. Makra uniemożliwiają dalsze przetwarzanie niepoprawne parametry w kodzie. W odróżnieniu od **ASSERT** makra, **upewnij się, że** makra zgłosić wyjątek, oprócz generowania potwierdzenia.  
  
 Makra zachowują się na dwa sposoby, w zależności od konfiguracji projektu. Wywołanie makra **ASSERT** i następnie zgłosić wyjątek, jeśli potwierdzenie nie powiedzie się. W związku z tym w konfiguracji debugowania (oznacza to, gdzie **_DEBUG** jest zdefiniowana) makra tworzyć potwierdzenia i wyjątków w wersji konfiguracji, makra tworzy tylko wyjątek (**ASSERT** nie obliczenia wyrażenia w konfiguracjach wersji).  
  
 Makro **ENSURE_ARG** działa jak **upewnij się, że** makra.  
  
 **ENSURE_VALID** wywołania `ASSERT_VALID` makra (co ma wpływ tylko w kompilacjach debugowania). Ponadto **ENSURE_VALID** zgłasza wyjątek, jeśli wskaźnik jest pusty. Test wartość NULL jest wykonywane w konfiguracjach zarówno Debug i Release.  
  
 Jeśli którakolwiek z tych testów kończy się niepowodzeniem, zostanie wyświetlony komunikat alertu w taki sam sposób jak **ASSERT**. Makro zgłasza wyjątek nieprawidłowego argumentu, w razie potrzeby.  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [SPRAWDŹ](#verify)   
 [ATLENSURE](#altensure)

## <a name="this_file"></a> THIS_FILE —
Rozwija do nazwy pliku, który jest kompilowany.  
   
### <a name="syntax"></a>Składnia    
```
THIS_FILE    
```  
   
### <a name="remarks"></a>Uwagi  
 Te informacje są używane przez **ASSERT** i **Sprawdź** makra. Kreatorzy Kreatora aplikacji i kod umieść makra plików kodu źródłowego, które tworzą.  
   
### <a name="example"></a>Przykład  
```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the 
// compiler recognizes. 
```
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [ASSERT](#assert)   
 [SPRAWDŹ](#verify)


##  <a name="trace"></a>  ŚLEDZENIA  
 Wysyła podany ciąg do debugera w bieżącej aplikacji.  
  
```   
TRACE(exp)  
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)   
```  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) opis **śledzenia**. **ŚLEDZENIA** i `ATLTRACE2` ma takie samo zachowanie.  
  
 W wersji do debugowania MFC to makro wysyła określony ciąg do debugera w bieżącej aplikacji. W kompilacji wydania to makro kompiluje się na wartość nothing (nie jest wygenerowano kodu w ogóle).  
  
 Aby uzyskać więcej informacji, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h

##  <a name="verify"></a>  SPRAWDŹ  
 W wersji do debugowania MFC ocenia jej argument.  
  
```   
VERIFY(booleanExpression)   
```  
  
### <a name="parameters"></a>Parametry  
 `booleanExpression`  
 Określa wyrażenie (w tym wartości wskaźnika), którego wynikiem jest różna od zera lub równa 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wynik wynosi 0, makra drukuje wiadomość diagnostycznych i zatrzymuje program. Jeśli warunek nie jest różna od zera, go nie działa.  
  
 Komunikat diagnostycznych ma formularza  
  
 `assertion failed in file <name> in line <num>`  
  
 gdzie *nazwa* to nazwa pliku źródłowego i *num* jest numer wiersza to potwierdzenie, że nie powiodło się w pliku źródłowym.  
  
 W wydanej wersji programu MFC **Sprawdź** oblicza wyrażenie nie drukowania lub przerwania programu. Na przykład jeśli wyrażenie jest wywołanie funkcji, będzie nawiązywane wywołania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h

##  <a name="cdumpcontext_in_mfc"></a>  afxDump (CDumpContext w MFC)  
 Zapewnia podstawowe możliwości zrzucanie obiektów w aplikacji.  
  
```   
CDumpContext  afxDump;   
```  
  
### <a name="remarks"></a>Uwagi  
 `afxDump` jest wstępnie zdefiniowanej [CDumpContext](../../mfc/reference/cdumpcontext-class.md) obiekt, który pozwala na wysyłanie `CDumpContext` informacji w oknie danych wyjściowych debugera lub terminal debugowania. Zwykle, podaj `afxDump` jako parametr `CObject::Dump`.  
  
 W systemach Windows NT i wszystkich wersji systemu Windows `afxDump` dane wyjściowe są wysyłane do okna danych wyjściowych debugowania Visual c++ podczas debugowania aplikacji.  
  
 Ta zmienna jest zdefiniowana tylko w wersji do debugowania MFC. Aby uzyskać więcej informacji na temat `afxDump`, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h


## <a name="afxdump"></a> Afxdump — (wewnętrzny)
Wewnętrzna funkcja MFC używa do zrzutu stan obiektu podczas debugowania.  

### <a name="syntax"></a>Składnia    
```
void AfxDump(const CObject* pOb);   
```
### <a name="parameters"></a>Parametry  
 `pOb`  
 Wskaźnik do obiektu klasy pochodzące z `CObject`.  
   
### <a name="remarks"></a>Uwagi  
 **Afxdump —** wywołuje obiekt `Dump` funkcji Członkowskich i wysyła informacje do lokalizacji określonej przez `afxDump` zmiennej. **Afxdump —** jest dostępna tylko w wersji do debugowania MFC.  
  
 Kod program nie powinien wywoływać **afxdump —**, ale zamiast tego należy wywołać `Dump` funkcji członkowskiej klasy odpowiedniego obiektu.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
   
### <a name="see-also"></a>Zobacz też  
 [CObject::Dump](cobject-class.md#dump)   



##  <a name="afxmemdf"></a>  afxmemdf —  
 Ta zmienna jest dostępny z debugera lub program i pozwala dostosować diagnostyki alokacji.  
  
```   
int  afxMemDF;  
```  
  
### <a name="remarks"></a>Uwagi  
 `afxMemDF` może mieć następujące wartości zgodnie z wyliczenia `afxMemDF`:  
  
- **allocmemdf —** Włącza debugowanie alokatora (ustawienie domyślne w bibliotek debugowania).  
  
- **delayfreememdf —** opóźnienia zwalnianie pamięci. Podczas programu zwalnia blok pamięci, program przydzielania nie zwraca pamięci, aby system operacyjny. To spowoduje umieszczenie obciążenia maksymalna ilość pamięci programu.  
  
- **checkalwaysmemdf —** wywołania `AfxCheckMemory` każdorazowo pamięci są przydzielone lub zwolniony. Spowoduje to znaczne spowolnienie alokacji pamięci i dezalokacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h

##  <a name="afxcheckerror"></a>  Afxcheckerror —  
 Ta funkcja sprawdza przekazany **SCODE** można sprawdzić, czy jest błąd.  
  
```   
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException* 
throw COleException*  
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli występuje błąd, funkcja zwraca wyjątek. Jeśli przekazany `SCODE` jest **E_OUTOFMEMORY**, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) przez wywołanie metody [afxthrowmemoryexception —](exception-processing.md#afxthrowmemoryexception). W przeciwnym razie funkcja zwraca [COleException](../../mfc/reference/coleexception-class.md) przez wywołanie metody [afxthrowoleexception —](exception-processing.md#afxthrowoleexception).  
  
 Tej funkcji można używać do sprawdzania wartości zwracanych metody wywołania funkcji OLE w aplikacji. Testując wartość zwracaną z tej funkcji w aplikacji, można prawidłowo reagują na warunki błędu z minimalną ilością kodu.  
  
> [!NOTE]
>  Ta funkcja działa tak samo w debugowania i tworzy bez debugowania.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h

##  <a name="afxcheckmemory"></a>  Afxcheckmemory —  
 Ta funkcja weryfikuje puli pamięci i wyświetla komunikaty o błędach, zgodnie z wymaganiami.  
  
```   
BOOL  AfxCheckMemory(); 
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli żadne błędy pamięci; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli funkcja wykryje nie uszkodzenie pamięci, drukuje nothing.  
  
 Wszystkie bloki pamięci obecnie przydzielony na stosie są zaznaczone, łącznie z tymi przydzielonej przez **nowe** , ale nie przyznanych przez bezpośrednie wywołania do podstawowej pamięci allocators —, takich jak `malloc` funkcji lub  **Działanie funkcji GlobalAlloc** funkcji systemu Windows. W przypadku bloku jest uszkodzony, wiadomość jest drukowana danych wyjściowych debugera.  
  
 Jeśli dołączysz wiersza  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]  
  
 w module programu, następnie kolejnych wywołań `AfxCheckMemory` Pokaż nazwę i numer wiersza, gdzie została przydzielona pamięć.  
  
> [!NOTE]
>  Jeśli modułu zawiera jeden lub więcej implementacje klas możliwych do serializacji, a następnie możesz umieścić `#define` wiersza po ostatniej `IMPLEMENT_SERIAL` wywołanie makra.  
  
 Ta funkcja działa tylko w wersji do debugowania MFC.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
 
##  <a name="afxdump"></a>  Afxdump — (MFC)  
 Wywołanie tej funkcji w debugera zrzutu stan obiektu podczas debugowania.  
  
```   
void AfxDump(const CObject* pOb); 
```  
  
### <a name="parameters"></a>Parametry  
 `pOb`  
 Wskaźnik do obiektu klasy pochodzące z `CObject`.  
  
### <a name="remarks"></a>Uwagi  
 **Afxdump —** wywołuje obiekt `Dump` funkcji Członkowskich i wysyła informacje do lokalizacji określonej przez `afxDump` zmiennej. **Afxdump —** jest dostępna tylko w wersji do debugowania MFC.  
  
 Kod program nie powinien wywoływać **afxdump —**, ale zamiast tego należy wywołać `Dump` funkcji członkowskiej klasy odpowiedniego obiektu.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  

### <a name="see-also"></a>Zobacz też  
 [CObject::Dump](cobject-class.md#dump)   


  
##  <a name="afxdumpstack"></a>  Afxdumpstack —  
 Ta funkcja globalna umożliwia generowanie obrazu bieżącego stosu.  
  
```   
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT); 
```  
  
### <a name="parameters"></a>Parametry  
 *dwTarget*  
 Wskazuje element docelowy zrzutu dane wyjściowe. Możliwe wartości, które można łączyć, używając wartości bitowe lub ( **&#124;**) operatora, są następujące:  
  
- **AFX_STACK_DUMP_TARGET_TRACE** wysyła dane wyjściowe za pomocą klasy [śledzenia](#trace) makra. **Śledzenia** makro generuje dane wyjściowe w tylko kompilacje typu debug; generuje żadnych danych wyjściowych w kompilacjach wydania. Ponadto **śledzenia** mogą zostać przekierowane do innych celów poza debugerem.  
  
- **AFX_STACK_DUMP_TARGET_DEFAULT** wysyła zrzut danych wyjściowych do domyślnego obiektu docelowego. Do kompilacji debugowanej, dane wyjściowe przechodzi do **śledzenia** makra. W kompilacji wydania wyjścia przejdzie do Schowka.  
  
- **AFX_STACK_DUMP_TARGET_CLIPBOARD** wysyła dane wyjściowe tylko do Schowka. Dane są umieszczane w Schowku jako zwykły tekst przy użyciu **CF_TEXT** formatu Schowka.  
  
- **AFX_STACK_DUMP_TARGET_BOTH** wysyła dane wyjściowe do Schowka oraz na **śledzenia** makra, jednocześnie.  
  
- **AFX_STACK_DUMP_TARGET_ODS** wysyła dane wyjściowe bezpośrednio do debugera za pomocą funkcji Win32 **OutputDebugString()**. Ta opcja spowoduje generowania danych wyjściowych debugera w obu debugowania i wydania kompilacji, gdy debuger jest dołączony do procesu. **AFX_STACK_DUMP_TARGET_ODS** zawsze osiągnie debugera (jeśli jest on podłączony) i nie może zostać przekierowane.  
  
### <a name="remarks"></a>Uwagi  
 W poniższym przykładzie odzwierciedla pojedynczy wiersz danych wyjściowych wygenerowanych z wywołaniem `AfxDumpStack` z obsługi przycisku w oknie dialogowym MFC aplikacji:  
  
 `=== begin AfxDumpStack output ===`  
  
 `00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes`  
  
 `0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes`  
  
 `0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,`  
  
 `unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct AFX_CMDHANDLE`  
  
 `0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes`  
  
 `00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned`  
  
 `int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes`  
  
 `00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned`  
  
 `int,long) + 312 bytes`  
  
 `00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned`  
  
 `int,unsigned int,long,long *) + 83 bytes`  
  
 `00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned`  
  
 `int,unsigned int,long) + 46 bytes`  
  
 `004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct`  
  
 `HWND__ *,unsigned int,unsigned int,long) + 237 bytes`  
  
 `00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned`  
  
 `int,unsigned int,long) + 129 bytes`  
  
 `BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes`  
  
 `BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes`  
  
 `=== end AfxDumpStack() output ===`  
  
 Każdy wiersz w powyższych danych wyjściowych wskazuje adres ostatniego wywołania funkcji, pełna nazwa ścieżki modułu, który zawiera wywołanie funkcji i prototypu funkcji o nazwie. Jeśli wywołanie funkcji na stosie nie odbywa się pod adresem dokładne funkcji, przesunięcia bajtów jest wyświetlany.  
  
 Na przykład w poniższej tabeli opisano w pierwszym wierszu powyżej dane wyjściowe:  
  
|Dane wyjściowe|Opis|  
|------------|-----------------|  
|`00427D55:`|Adres zwrotny ostatniego wywołania funkcji.|  
|`DUMP2\DEBUG\DUMP2.EXE!`|Nazwa pełnej ścieżki moduł, który zawiera wywołanie funkcji.|  
|`void AfxDumpStack(unsigned long)`|Prototyp funkcji o nazwie.|  
|`+ 181 bytes`|Przesunięcie w bajtach z adresu prototypu funkcji (w tym przypadku `void AfxDumpStack(unsigned long)`) na adres zwrotny (w tym przypadku `00427D55`).|  
  
 `AfxDumpStack` jest dostępna w wersjach debugowania i nondebug biblioteki MFC; Jednak funkcja jest zawsze połączony statycznie, nawet wtedy, gdy plik wykonywalny używa MFC w współdzielonej bibliotece DLL. W implementacji biblioteki udostępnione funkcji znajduje się w MFCS42. Biblioteki LIB (i jej wariantów).  
  
 Aby pomyślnie użyć tej funkcji:  
  
-   Plik IMAGEHLP. Biblioteki DLL muszą być na ścieżce. Jeśli nie masz tę bibliotekę DLL, funkcja wyświetli komunikat o błędzie. Zobacz [biblioteki Pomocy obrazu](http://msdn.microsoft.com/library/windows/desktop/ms680321) dla informacji na temat zestawu funkcji dostarczonych przez IMAGEHLP.  
  
-   Moduły, które mają ramek na stosie musi zawierać informacje o debugowaniu. Jeśli nie zawierają informacji o debugowaniu, funkcja nadal wygeneruje ślad stosu, ale będzie mniej szczegółowe dane śledzenia.  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="afxenablememoryleakdump"></a>  Afxenablememoryleakdump —  
 Włącza i wyłącza zrzut przeciek pamięci w `AFX_DEBUG_STATE` destruktora.  
  
```  
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```  
  
### <a name="parameters"></a>Parametry  
 [in] `bDump`  
 `TRUE` Wskazuje, że zrzut przeciek pamięci jest włączone; `FALSE` wskazuje zrzut przeciek pamięci jest wyłączona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednia wartość tej flagi.  
  
### <a name="remarks"></a>Uwagi  
 Gdy aplikacja zwalnia biblioteki MFC, biblioteki MFC sprawdza przecieki pamięci. W tym momencie żadnych przecieki pamięci są zgłaszane za pośrednictwem **debugowania** okna [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  
  
 Jeśli aplikacja ładuje inną biblioteką przed biblioteki MFC, niektóre alokacji pamięci w tej biblioteki będą niepoprawnie raportowane jako przecieki pamięci. Przecieki pamięci false może spowodować Zamknij powoli jako biblioteki MFC raporty ich aplikacji. W takim przypadku należy użyć `AfxEnableMemoryLeakDump` wyłączyć zrzut przeciek pamięci.  
  
> [!NOTE]
>  Jeśli ta metoda umożliwia wyłączanie zrzut przeciek pamięci, nie otrzymasz raporty przecieki pamięci prawidłowy w aplikacji. Tej metody należy używać tylko, jeśli masz pewność, że raport przeciek pamięci zawiera przecieki pamięci wartość false.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="afxenablememorytracking"></a>  Afxenablememorytracking —  
 W wersji do debugowania MFC zwykle włączono pamięci diagnostycznych śledzenia.  
  
```   
BOOL AfxEnableMemoryTracking(BOOL bTrack); 
```  
  
### <a name="parameters"></a>Parametry  
 *bTrack*  
 Ustawienie tej wartości na **TRUE** powoduje włączenie śledzenia; pamięci **FALSE** powoduje wyłączenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednie ustawienie flagi śledzenia Włącz.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej funkcji, aby wyłączyć śledzenie na sekcje, o którym wiadomo, że są poprawnie przydzielanie bloków kodu.  
  
 Aby uzyskać więcej informacji na temat `AfxEnableMemoryTracking`, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Ta funkcja działa tylko w wersji do debugowania MFC.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="afxismemoryblock"></a>  Afxismemoryblock —  
 Sprawdzenie adres pamięci, aby się upewnić, że reprezentuje blok aktualnie aktywnej pamięci alokowanej przez wersję diagnostycznych **nowe**.  
  
```   
BOOL AfxIsMemoryBlock(
    const void* p,  
    UINT nBytes,  
    LONG* plRequestNumber = NULL); 
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskazuje blok pamięci do sprawdzenia.  
  
 `nBytes`  
 Zawiera długość Blok pamięci w bajtach.  
  
 `plRequestNumber`  
 Wskazuje **długi** liczba całkowita, która zostanie wprowadzona numer sekwencji alokacji blok pamięci lub zero, jeśli nie reprezentuje blok aktualnie aktywnej pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli blok pamięci jest aktualnie przydzielona, a długość jest prawidłowa; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Sprawdza również określony rozmiar względem oryginalnego przydzielony rozmiar. Jeśli funkcja zwraca wartość niezerową, numer sekwencji alokacji jest zwracany w `plRequestNumber`. Liczba ta reprezentuje kolejność, w której przydzielono bloku względem wszystkich innych **nowe** alokacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="afxisvalidaddress"></a>  Afxisvalidaddress —  
 Testy dowolny adres pamięci, aby upewnić się, że znajduje się całkowicie w obszarze pamięci programu.  
  
```   
BOOL AfxIsValidAddress(
    const void* lp,  
    UINT nBytes,  
    BOOL bReadWrite = TRUE); 
```  
  
### <a name="parameters"></a>Parametry  
 `lp`  
 Wskazuje adres pamięci do sprawdzenia.  
  
 `nBytes`  
 Zawiera liczbę bajtów pamięci do sprawdzenia.  
  
 *bReadWrite*  
 Określa, czy pamięć jest zarówno do odczytu i zapisu ( **TRUE**) lub tylko czytać ( **FALSE**).  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania różną od zera, jeśli zablokowanie określony rozmiar pamięci jest całkowicie zawarty w obszarze pamięci programu; w przeciwnym razie 0.  
  
 W kompilacjach do debugowania z systemem innym niż różna od zera, jeśli `lp` nie jest wartość NULL; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Adres nie jest ograniczone do bloków przydzielonej przez **nowe**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="afxisvalidstring"></a>  Afxisvalidstring —  
 Ta funkcja służy do określenia, czy wskaźnik do ciągu jest prawidłowy.  
  
```   
BOOL  AfxIsValidString(
    LPCSTR lpsz,  
    int nLength = -1); 
```  
  
### <a name="parameters"></a>Parametry  
 `lpsz`  
 Wskaźnik do testowania.  
  
 `nLength`  
 Określa długość ciągu do sprawdzenia, w bajtach. Wartość -1 wskazuje, że ciąg będzie zerem.  
  
### <a name="return-value"></a>Wartość zwracana  
 W kompilacjach do debugowania różną od zera, jeśli określony wskaźnik wskazuje ciąg o określonym rozmiarze; w przeciwnym razie 0.  
  
 W kompilacjach do debugowania z systemem innym niż różna od zera, jeśli `lpsz` nie jest wartość NULL; w przeciwnym razie wartość 0.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="afxsetallochook"></a>  Afxsetallochook —  
 Ustawia haku, umożliwiającą wywoływania określona funkcja przed każdy blok pamięci są przydzielone.  
  
```   
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook); 
```  
  
### <a name="parameters"></a>Parametry  
 *pfnAllocHook*  
 Określa nazwę funkcji do wywołania. Zobacz uwagi dla prototypu funkcji alokacji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli chcesz zezwolić na alokację; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Microsoft Foundation Class Library debugowania-alokatora można wywołać funkcję haku zdefiniowane przez użytkownika umożliwia użytkownikom do monitorowania alokacji pamięci oraz do sterowania, czy przydział jest dozwolone. Funkcje punktu zaczepienia alokacji są prototypowana w następujący sposób:  
  
 **Wartość logiczna AFXAPI AllocHook (size_t** `nSize` **, BOOL** `bObject` **długim** `lRequestNumber` **);**  
  
 `nSize`  
 Rozmiar alokacji pamięci proponowanych.  
  
 `bObject`  
 **Wartość TRUE,** w przypadku alokacji dla `CObject`-pochodnych obiektu; w przeciwnym razie **FALSE**.  
  
 `lRequestNumber`  
 Numer sekwencyjny alokacji pamięci.  
  
 Należy pamiętać, że **AFXAPI** konwencji wywoływania oznacza wywoływany musisz usunąć parametry ze stosu.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="afxdoforallclasses"></a>  Afxdoforallclasses —  
 Wywołuje funkcję iteracji określony dla wszystkich serializacji `CObject`-pochodnych klas w przestrzeni pamięci aplikacji.  
  
```   
void  
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parametry  
 `pfn`  
 Wskazuje iteracji funkcja wywoływana dla każdej klasy. Argumenty funkcji są wskaźnik do `CRuntimeClass` obiekt i void wskaźnik do wywołującego dostarcza funkcji dodatkowe dane.  
  
 `pContext`  
 Wskazuje opcjonalnymi danymi, które obiekt wywołujący może dostarczać funkcji iteracji. This, wskaźnik może być **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Możliwy do serializacji `CObject`-klas pochodnych są klasy pochodne przy użyciu `DECLARE_SERIAL` makra. Wskaźnik, który jest przekazywany do `AfxDoForAllClasses` w `pContext` jest przekazywany do funkcji określonej iteracji zawsze jest ona wywoływana.  
  
> [!NOTE]
>  Ta funkcja działa tylko w wersji do debugowania MFC.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h 

##  <a name="afxdoforallobjects"></a>  Afxdoforallobjects —  
 Wykonuje funkcję iteracji określony dla wszystkich obiektów pochodzących z `CObject` przydzielonych z **nowe**.  
  
```   
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),  
    void* pContext); 
```  
  
### <a name="parameters"></a>Parametry  
 `pfn`  
 Wskazuje iteracji funkcja do wykonania dla każdego obiektu. Argumenty funkcji są wskaźnik do `CObject` i void wskaźnik do wywołującego dostarcza funkcji dodatkowe dane.  
  
 `pContext`  
 Wskazuje opcjonalnymi danymi, które obiekt wywołujący może dostarczać funkcji iteracji. This, wskaźnik może być **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Nie wyliczyć stosu globalnych lub osadzonych obiektów. Wskaźnik przekazany do `AfxDoForAllObjects` w `pContext` jest przekazywany do funkcji określonej iteracji zawsze jest ona wywoływana.  
  
> [!NOTE]
>  Ta funkcja działa tylko w wersji do debugowania MFC.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]  
  
 [!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)