---
title: Usługi diagnostyczne
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
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
ms.openlocfilehash: a4979ab7bbc0e396de5629fba1b86f3bfb602dcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322725"
---
# <a name="diagnostic-services"></a>Usługi diagnostyczne

Biblioteki klas Microsoft Foundation dostarcza wiele usługi diagnostyczne, które programy łatwiejsze debugowanie. Te usługi diagnostyczne zawierają makra i funkcje globalne, które umożliwiają śledzenie pamięci programu alokacji, zrzutu zawartość obiektów w czasie wykonywania i Drukuj komunikaty debugowania w czasie wykonywania. Makra i funkcje globalne dla usługi diagnostyczne są podzielone na następujące kategorie:

- Ogólne makra diagnostyczne

- Ogólne funkcje diagnostyczne i zmienne

- Funkcje diagnostyczne obiektów

Te makra i funkcje są dostępne dla wszystkich klas pochodnych `CObject` w Debug i Release wersje biblioteki MFC. Jednak wszystkie z wyjątkiem DEBUG_NEW i sprawdź, czy nic nie rób w pełnej wersji.

W bibliotece debugowania wszystkie bloki ilość przydzielonej pamięci jest oddzielona z serii "guard bajtów." Jeśli bajty te są zakłócony zapisu wadliwe pamięci, procedur diagnostycznych może zgłosić problem. Jeśli dołączysz wiersz:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

w pliku implementacji wszystkich wywołań **nowe** zapisze numer nazwę pliku i wierszu, w którym nastąpiło alokacji pamięci. Funkcja [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) wyświetli te informacje dodatkowe, umożliwiając identyfikacji przecieków pamięci. Zapoznaj się również w klasie [CDumpContext](../../mfc/reference/cdumpcontext-class.md) dodatkowe informacje na temat diagnostyczne dane wyjściowe.

Ponadto biblioteki wykonawczej C obsługuje również zestaw funkcji diagnostycznych, które służy do debugowania aplikacji. Aby uzyskać więcej informacji, zobacz [debugować procedury](../../c-runtime-library/debug-routines.md) w odwołaniu biblioteki wykonawczej.

### <a name="mfc-general-diagnostic-macros"></a>Makra diagnostyczne ogólne MFC

|||
|-|-|
|[ASSERT](#assert)|Drukuje wiadomość, a następnie przerywa program, jeśli określone wyrażenie zwróci wartość FALSE w wersji do debugowania biblioteki.|
|[ASSERT_KINDOF](#assert_kindof)|Testy, które obiekt to obiekt określonej klasy lub klasy pochodzącej od określonej klasy.|
|[ASSERT_VALID](#assert_valid)|Sprawdza poprawność wewnętrznego obiektu przez wywołanie jego `AssertValid` funkcję członkowską; zazwyczaj zgodnym z przesłoniętą z `CObject`.|
|[DEBUG_NEW](#debug_new)|Zawiera nazwę pliku i numer wiersza dla wszystkich alokacji obiektów w trybie debugowania do znajdowania przecieki pamięci.|
|[DEBUG_ONLY](#debug_only)|Podobnie jak ASSERT, ale nie sprawdza wartość wyrażenia. przydatne dla kodu, które mają być wykonywane tylko w trybie debugowania.|
|[Upewnij się, że i ENSURE_VALID](#ensure)|Użyj, aby sprawdzić poprawność danych.|
|[THIS_FILE](#this_file)|Rozwija się do nazwy pliku który jest kompilowany.|
|[ŚLEDZENIA](#trace)|Udostępnia `printf`— możliwości są dostępne w wersji do debugowania biblioteki, takie jak.|
|[SPRAWDŹ](#verify)|Podobnie jak ASSERT ale oblicza wyrażenie w wersji biblioteki, a także w wersji do debugowania.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Funkcje i zmienne Diagnostyka ogólnego MFC

|||
|-|-|
|[afxDump](#afxdump)|Zmienna globalna, która wysyła [CDumpContext](../../mfc/reference/cdumpcontext-class.md) informacji w oknie danych wyjściowych debugera lub terminalu debugowania.|
|[afxMemDF](#afxmemdf)|Zmienna globalna, która steruje zachowaniem debugowanie alokatora pamięci.|
|[AfxCheckError](#afxcheckerror)|Zmienna globalna, używane do testowania SCODE sukces, aby zobaczyć, jeśli jest to błąd, a jeśli tak, zgłasza odpowiedni komunikat o błędzie.|
|[AfxCheckMemory](#afxcheckmemory)|Sprawdza, czy integralność wszystkich aktualnie przydzielonej pamięci.|
|[AfxDebugBreak](#afxdebugbreak)|Powoduje przerwanie wykonywania.|
|[AfxDump](#cdumpcontext_in_mfc)|Jeśli jest wywoływana, gdy w debugerze, zrzuty stanu obiektu podczas debugowania.|
|[AfxDump](#afxdump)|Funkcja wewnętrznego zrzuty stanu obiektu podczas debugowania.|
|[AfxDumpStack](#afxdumpstack)|Wygeneruj obraz bieżącego stosu. Ta funkcja jest zawsze połączone statycznie.|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|Umożliwia zrzut przecieku pamięci.|
|[Afxenablememorytracking —](#afxenablememorytracking)|Włącza śledzenie i wyłączanie pamięci.|
|[AfxIsMemoryBlock](#afxismemoryblock)|Weryfikuje, że blok pamięci został poprawnie przydzielony.|
|[AfxIsValidAddress](#afxisvalidaddress)|Weryfikuje, czy zakres adresów pamięci w granicach tego programu.|
|[Afxisvalidstring —](#afxisvalidstring)|Określa, czy wskaźnik do ciągu jest prawidłowy.|
|[AfxSetAllocHook](#afxsetallochook)|Umożliwia wywołanie funkcji na każdej alokacji pamięci.|

### <a name="mfc-object-diagnostic-functions"></a>Funkcje diagnostyczne obiektów MFC

|||
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|Wykonuje określoną funkcję na wszystkie `CObject`-pochodne klasy, które obsługują sprawdzanie typu run-time.|
|[AfxDoForAllObjects](#afxdoforallobjects)|Wykonuje określoną funkcję na wszystkie `CObject`-pochodnych obiektów przydzielonych za pomocą **nowe**.|

### <a name="mfc-compilation-macros"></a>Makra kompilacji MFC

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Pomija ostrzeżeń kompilatora do użytku zaniechanych funkcji MFC.|

## <a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS

Pomija ostrzeżeń kompilatora do użytku zaniechanych funkcji MFC.

### <a name="syntax"></a>Składnia

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Przykład

Ten przykładowy kod spowodują ostrzeżenia kompilatora, jeśli nie zdefiniowano _AFX_SECURE_NO_WARNINGS.

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

## <a name="afxdebugbreak"></a> AfxDebugBreak

Wywołaj tę funkcję, aby spowodować przerwanie (w miejscu wywołania `AfxDebugBreak`) podczas wykonywania wersji debugowania aplikacji MFC.

### <a name="syntax"></a>Składnia

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Uwagi

`AfxDebugBreak` nie ma wpływu na wersje aplikacji MFC i powinna zostać usunięta. To funkcja powinna być używana tylko w aplikacjach MFC. Użyj wersji interfejsu API Win32 `DebugBreak`, aby spowodować przerwy w aplikacjach innych niż MFC.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxver_.h

##  <a name="assert"></a>  ASSERT

Ocenia argument.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Określa wyrażenie (w tym wartości wskaźnika), którego wynikiem jest wartość różną od zera lub równa 0.

### <a name="remarks"></a>Uwagi

Jeśli wynik jest równy 0, makro wyświetla komunikat diagnostyczny i przerywa program. Jeśli warunek ma wartość różną od zera, nic nie robi.

Komunikat diagnostyczny ma postać

`assertion failed in file <name> in line <num>`

gdzie *nazwa* to nazwa pliku źródłowego i *num* jest numer wiersza potwierdzenie, że nie powiodło się w pliku źródłowym.

W wersji MFC ASERCJA nie może oszacować wyrażenia i dlatego nie przerywa program. Jeśli można obliczyć wyrażenia, niezależnie od tego, w środowisku, należy użyć makro VERIFY zamiast ASSERT.

> [!NOTE]
>  Ta funkcja jest dostępna tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="assert_kindof"></a>  ASSERT_KINDOF

To makro potwierdza, że obiekt wskazany obiekt określonej klasy lub jest tworzony obiekt klasy na podstawie określonej klasy.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Parametry

*classname*<br/>
Nazwa `CObject`-klasy pochodnej.

*pobject*<br/>
Wskaźnik do obiektu klasy.

### <a name="remarks"></a>Uwagi

*Obiekt* parametr powinien być wskaźnik do obiektu i może być **const**. Obiekt wskazywany i klasy musi obsługiwać `CObject` informacji o klasie czasu wykonywania. Jako przykład, aby upewnić się, że `pDocument` jest wskaźnikiem do obiektu `CMyDoc` klasy lub dowolnego z jego pochodne mogą kodu:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

Za pomocą `ASSERT_KINDOF` — makro jest dokładnie taka sama, jak kodowanie:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Ta funkcja działa tylko w przypadku klasy zadeklarowane za pomocą [DECLARE_DYNAMIC] (Uruchom — czasu — obiekt model-services.md #declare_dynamic lub [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) makra.

> [!NOTE]
>  Ta funkcja jest dostępna tylko w wersji debugowania MFC.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="assert_valid"></a>  ASSERT_VALID

Użycie w celu przetestowania założeń dotyczących ważności stanu wewnętrznego obiektu.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Parametry

*pObject*<br/>
Określa obiekt klasy pochodzącej od `CObject` zawierający nadrzędnych wersję `AssertValid` funkcja elementu członkowskiego.

### <a name="remarks"></a>Uwagi

ASSERT_VALID wywołania `AssertValid` funkcja elementu członkowskiego obiektu jest przekazywany jako argument.

W wersji MFC ASSERT_VALID nic nie robi. W wersji debugowania go sprawdza poprawność wskaźnika, sprawdza, czy mają wartości null i wywołuje własnego obiektu `AssertValid` funkcji elementów członkowskich. Jeśli któregoś z powyższych testów kończy się niepowodzeniem, zostanie wyświetlony komunikat alertu, w taki sam sposób jak [ASERCJA](#assert).

> [!NOTE]
>  Ta funkcja jest dostępna tylko w wersji debugowania MFC.

Aby uzyskać więcej informacji i przykładów, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="debug_new"></a>  DEBUG_NEW

Ułatwia znajdowanie przecieków pamięci.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Uwagi

DEBUG_NEW można użyć wszędzie, gdzie w programach, które normalnie zostałyby użyte **nowe** operatora do przydzielania pamięci sterty.

W trybie debugowania (gdy **_DEBUG** symboli jest zdefiniowana), DEBUG_NEW śledzi informacje o nazwę pliku i numer wiersza dla każdego obiektu, który go przydziela. Następnie, kiedy używasz [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) funkcji członkowskiej, każdy obiekt przydzielony za pomocą DEBUG_NEW jest wyświetlana przy użyciu nazwy pliku i numer wiersza której zostało przydzielone.

Aby użyć DEBUG_NEW, Wstaw następujące dyrektywy do plików źródłowych:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Po wstawieniu ta dyrektywa preprocesora zostanie wstawiona DEBUG_NEW wszędzie tam, gdzie możesz użyć **nowe**, a MFC zajmie się resztą. Podczas kompilowania wersji programu DEBUG_NEW jest rozpoznawana jako prosty **nowe** operacji i nazwę pliku i wierszu informacji liczb nie są generowane.

> [!NOTE]
>  W poprzednich wersjach programu MFC (4.1 i starszych) niezbędna do umieszczenia `#define` instrukcji znajdującej się po wszystkich instrukcji, które wywołały IMPLEMENT_DYNCREATE lub IMPLEMENT_SERIAL makra. To nie jest już konieczne.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="debug_only"></a>  DEBUG_ONLY

W trybie debugowania (gdy **_DEBUG** symboli jest zdefiniowana), DEBUG_ONLY ocenia jej argument.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Uwagi

W kompilacji wydania DEBUG_ONLY nie może oszacować jej argument. Jest to przydatne, gdy masz kod, który ma być wykonany tylko w kompilacjach do debugowania.

DEBUG_ONLY — makro jest odpowiednikiem otaczającego *wyrażenie* z `#ifdef _DEBUG` i `#endif`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

### <a name="ensure"></a>  Upewnij się, że i ENSURE_VALID

Użyj, aby sprawdzić poprawność danych.

### <a name="syntax"></a>Składnia

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Określa wyrażenie logiczne do zbadania.

### <a name="remarks"></a>Uwagi

Te makra ma na celu poprawę sprawdzanie poprawności parametrów. Makra uniemożliwiają dalsze przetwarzanie niepoprawne parametry w kodzie. W przeciwieństwie do makra ASSERT upewnij się, że makra zgłosić wyjątek oprócz generowania potwierdzenie.

Makra zachowują się na dwa sposoby, zgodnie z konfiguracją projektu. Makra ASSERT wywołania i następnie Zgłoś wyjątek, jeśli potwierdzenie nie powiedzie się. W związku z tym konfiguracji debugowania (gdzie definiuje się _DEBUG) makra do tworzenia potwierdzenia i wyjątek podczas w konfiguracjach wersji produktu makra wyjątek (ASERCJA nie może oszacować wyrażenia w konfiguracjach wersji).

Makro ENSURE_ARG zachowuje się jak makro upewnij się, że.

ENSURE_VALID wywołuje ASSERT_VALID — makro (który ma wpływ tylko w kompilacjach do debugowania). Ponadto ENSURE_VALID zgłasza wyjątek, jeśli wskaźnik jest pusty. Test o wartości NULL jest wykonywane w konfiguracji Debug i Release.

Jeśli którykolwiek z tych testów nie powiedzie się, komunikat alertu jest wyświetlany w taki sam sposób jak ASSERT. Makro zgłasza wyjątek nieprawidłowego argumentu, jeśli to konieczne.
### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="this_file"></a> THIS_FILE

Rozwija się do nazwy pliku który jest kompilowany.

### <a name="syntax"></a>Składnia

```
THIS_FILE
```

### <a name="remarks"></a>Uwagi

Informacje są używane przez makra ASSERT i sprawdź. Kreatory Kreatora aplikacji, a kod umieść makro w plikach kodu źródłowego, utworzonego przez siebie.

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

##  <a name="trace"></a>  TRACE

Wysyła podany ciąg do debugera w bieżącej aplikacji.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Uwagi

Zobacz [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) Opis śledzenia. ŚLEDZENIE i ATLTRACE2 mają takie samo zachowanie.

W wersji debugowania MFC to makro wysyła określony ciąg do debugera w bieżącej aplikacji. W kompilacji wydania to makro kompiluje, aby nic (nie wygenerowano żadnego kodu w ogóle).

Aby uzyskać więcej informacji, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="verify"></a>  SPRAWDŹ

W wersji debugowania MFC ocenia jej argument.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Określa wyrażenie (w tym wartości wskaźnika), którego wynikiem jest wartość różną od zera lub równa 0.

### <a name="remarks"></a>Uwagi

Jeśli wynik jest równy 0, makro wyświetla komunikat diagnostyczny i zatrzymuje program. Jeśli warunek ma wartość różną od zera, nic nie robi.

Komunikat diagnostyczny ma postać

`assertion failed in file <name> in line <num>`

gdzie *nazwa* jest nazwa pliku źródłowego i *num* jest numer wiersza potwierdzenie, że nie powiodło się w pliku źródłowym.

W wersji MFC Sprawdź, czy oblicza wyrażenie, ale nie wydrukować lub przerwania programu. Na przykład jeśli wyrażenie jest wywołanie funkcji, wywołania będą.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="cdumpcontext_in_mfc"></a>  afxDump (CDumpContext w MFC)

Zapewnia podstawowe możliwości zrzucania obiektów w aplikacji.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Uwagi

`afxDump` jest wstępnie zdefiniowanej [CDumpContext](../../mfc/reference/cdumpcontext-class.md) obiekt, który umożliwia wysyłanie `CDumpContext` informacji w oknie danych wyjściowych debugera lub terminalu debugowania. Zazwyczaj podajesz `afxDump` jako parametr do `CObject::Dump`.

W obszarze Windows NT i wszystkie wersje systemu Windows `afxDump` dane wyjściowe są wysyłane do okna danych wyjściowych debugowania programu Visual C++ podczas debugowania aplikacji.

Ta zmienna jest zdefiniowane tylko w wersji debugowania MFC. Aby uzyskać więcej informacji na temat `afxDump`, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxdump"></a> AfxDump (wewnętrzny)

Funkcja wewnętrznego MFC wykorzystuje do porzucenia stanu obiektu podczas debugowania.

### <a name="syntax"></a>Składnia

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Wskaźnik do obiektu klasy pochodne `CObject`.

### <a name="remarks"></a>Uwagi

`AfxDump` wywołuje obiekt `Dump` funkcja elementu członkowskiego i wysyła informacje do lokalizacji określonej przez `afxDump` zmiennej. `AfxDump` jest dostępna tylko w wersji debugowania MFC.

Kodu programu nie powinien wywoływać `AfxDump`, ale zamiast tego należy wywołać `Dump` funkcji składowej typu odpowiedniego obiektu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxmemdf"></a>  afxMemDF

Ta zmienna jest dostępny z debugera lub z programu i pozwala na dostosowywanie diagnostyki alokacji.

```
int  afxMemDF;
```

### <a name="remarks"></a>Uwagi

`afxMemDF` może mieć następujące wartości określonych przez wyliczenie `afxMemDF`:

- `allocMemDF` Włącza debugowanie alokatora (ustawienie domyślne w bibliotek debugowania).

- `delayFreeMemDF` Zwalnianie pamięci opóźnienia. Gdy program zwalnia blok pamięci, alokator nie zwraca pamięci do zasadniczego systemu operacyjnego. Spowoduje to umieszczenie obciążenia maksymalna ilość pamięci programu.

- `checkAlwaysMemDF` Wywołania `AfxCheckMemory` za każdym razem, gdy przydzielone lub zwolnienie pamięci. Spowoduje to znaczne spowolnienie alokacje pamięci i cofnięcia alokacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxcheckerror"></a>  Afxcheckerror —

Ta funkcja sprawdza SCODE sukces, jeśli znajduje się błąd.

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Uwagi

Jeśli jest to błąd, funkcja zgłasza wyjątek. Jeśli przekazany SCODE E_OUTOFMEMORY, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) przez wywołanie metody [afxthrowmemoryexception —](exception-processing.md#afxthrowmemoryexception). W przeciwnym razie funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md) przez wywołanie metody [afxthrowoleexception —](exception-processing.md#afxthrowoleexception).

Ta funkcja może służyć do sprawdzania wartości zwracane wywołania funkcji OLE w aplikacji. Testując wartość zwracaną z tej funkcji w aplikacji, pozwala poprawnie reagować na błędy za pomocą minimalnej ilości kodu.

> [!NOTE]
>  Ta funkcja działa tak samo podczas debugowania i buduje bez debugowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxcheckmemory"></a>  AfxCheckMemory

Ta funkcja sprawdza poprawność puli wolnej pamięci i wyświetla komunikaty o błędach, zgodnie z potrzebami.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli żadne błędy pamięci; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli funkcja wykryje nie uszkodzenie pamięci, drukuje nothing.

Sprawdzane są wszystkie bloki pamięci aktualnie przydzielony na stosie, łącznie z tymi przydzielonej przez **nowe** , ale nie te, które przydzielonej przez bezpośrednie wywołania do bazowego buforów pamięci, takich jak **— funkcja malloc** funkcji lub `GlobalAlloc` funkcji Windows. Jeśli bloku znajduje się w uszkodzona, komunikat jest drukowany w danych wyjściowych debugera.

Jeśli dołączysz wiersza

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

w module programu, następnie kolejnych wywołań `AfxCheckMemory` Pokaż nazwę pliku i numer wiersza, gdzie pamięć została alokowana.

> [!NOTE]
>  Jeśli modułu zawiera co najmniej jeden implementacje klasy serializacji, a następnie należy umieścić `#define` wiersza po ostatnim wywołaniu IMPLEMENT_SERIAL — makro.

Ta funkcja działa tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxdump"></a>  AfxDump (MFC)

Wywołaj tę funkcję w debugera do porzucenia stanu obiektu podczas debugowania.

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Wskaźnik do obiektu klasy pochodne `CObject`.

### <a name="remarks"></a>Uwagi

`AfxDump` wywołuje obiekt `Dump` funkcja elementu członkowskiego i wysyła informacje do lokalizacji określonej przez `afxDump` zmiennej. `AfxDump` jest dostępna tylko w wersji debugowania MFC.

Kodu programu nie powinien wywoływać `AfxDump`, ale zamiast tego należy wywołać `Dump` funkcji składowej typu odpowiedniego obiektu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxdumpstack"></a>  Afxdumpstack —

Ta funkcja globalna może służyć do generowania obrazu bieżącego stosu.

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Parametry

*dwTarget*<br/>
Wskazuje obiekt docelowy danych wyjściowych zrzutu. Możliwe wartości, które można łączyć, używając Alternatywy bitowej ( **&#124;**) operator, są następujące:

- AFX_STACK_DUMP_TARGET_TRACE wysyła dane wyjściowe za [śledzenia](#trace) makra. TRACE — makro generuje dane wyjściowe w kompilacjach debugowania. generuje on żadnych danych wyjściowych w wydawanych wersjach. Ponadto śledzenia mogą zostać przekierowane do innych celów, oprócz debugera.

- Wysyła AFX_STACK_DUMP_TARGET_DEFAULT zrzutu dane wyjściowe do domyślnego obiektu docelowego. Dla kompilacji do debugowania danych wyjściowych trafia do TRACE — makro. W kompilacji wydania danych wyjściowych trafia do Schowka.

- AFX_STACK_DUMP_TARGET_CLIPBOARD wysyła dane wyjściowe tylko do Schowka. Dane są wklejane w Schowku jako zwykły tekst w formacie CF_TEXT Schowka.

- AFX_STACK_DUMP_TARGET_BOTH wysyła dane wyjściowe do Schowka i TRACE — makro, jednocześnie.

- AFX_STACK_DUMP_TARGET_ODS wysyła dane wyjściowe bezpośrednio do debugera za pomocą funkcji Win32 `OutputDebugString()`. Ta opcja spowoduje generowanie danych wyjściowych debugera w obu debugowania i kompilacje wydania, gdy debuger jest dołączony do procesu. AFX_STACK_DUMP_TARGET_ODS zawsze osiągnie debugera (jeśli jest on dołączony) i nie można przekierować.

### <a name="remarks"></a>Uwagi

W poniższym przykładzie odzwierciedla jednowierszowym dane wyjściowe generowane z wywołaniem `AfxDumpStack` z uchwyt przycisku w aplikacji MFC, okno dialogowe:

```Output
=== begin AfxDumpStack output ===
00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes
0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes
0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,
unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct
AFX_CMDHANDLE
0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes
00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes
00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned
int,long) + 312 bytes
00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned
int,unsigned int,long,long *) + 83 bytes
00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned
int,unsigned int,long) + 46 bytes
004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct
HWND__ *,unsigned int,unsigned int,long) + 237 bytes
00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned
int,unsigned int,long) + 129 bytes
BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes
BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes
=== end AfxDumpStack() output ===
```

Każdy wiersz w powyższych danych wyjściowych wskazuje adres ostatniego wywołania funkcji pełną nazwę ścieżki modułu, który zawiera wywołanie funkcji i prototypu funkcji o nazwie. W przypadku wywołania funkcji na stosie nie odbywa się pod adresem dokładnie funkcji, przesunięcia bajtów jest wyświetlana.

Na przykład w poniższej tabeli opisano pierwszy wiersz w powyższych danych wyjściowych:

|Dane wyjściowe|Opis|
|------------|-----------------|
|`00427D55:`|Adres zwrotny ostatniego wywołania funkcji.|
|`DUMP2\DEBUG\DUMP2.EXE!`|Pełna nazwa ścieżki modułu, który zawiera wywołanie funkcji.|
|`void AfxDumpStack(unsigned long)`|Prototyp funkcji jest wywoływana.|
|`+ 181 bytes`|Przesunięcie w bajtach od adres prototypu funkcji (w tym przypadku `void AfxDumpStack(unsigned long)`) na adres zwrotny (w tym przypadku `00427D55`).|

`AfxDumpStack` jest dostępna w wersji debugowania, jak i nondebug bibliotek MFC; Jednak funkcja zawsze jest połączona statycznie, nawet wtedy, gdy plik wykonywalny używa biblioteki MFC w współdzielonej bibliotece DLL. W implementacji Biblioteka udostępniona funkcja znajduje się w MFCS42. Biblioteki LIB (i jej wariantów).

Aby pomyślnie użyć tej funkcji:

- Plik IMAGEHLP. Biblioteka DLL musi być w zmiennej path. Jeśli nie masz tej biblioteki DLL, funkcja wyświetli komunikat o błędzie. Zobacz [biblioteki Pomocy obrazu](/windows/desktop/Debug/image-help-library) uzyskać informacji na temat zestawu funkcji dostarczonych przez IMAGEHLP.

- Moduły, które mają ramki na stosie musi zawierać informacje o debugowaniu. Jeśli nie zawierają informacji o debugowaniu, funkcja nadal wygeneruje ślad stosu, ale będzie mniej dokładny śledzenia.
  ### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxenablememoryleakdump"></a>  Afxenablememoryleakdump —

Włącza i wyłącza zrzut przecieku pamięci w destruktorze AFX_DEBUG_STATE.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Parametry

*bDump*<br/>
[in] Wartość TRUE wskazuje, że zrzut przecieku pamięci jest włączona; Wartość FALSE wskazuje, że zrzut przecieku pamięci jest wyłączona.

### <a name="return-value"></a>Wartość zwracana

Poprzedniej wartości tej flagi.

### <a name="remarks"></a>Uwagi

Gdy aplikacja zwalnia biblioteki MFC, biblioteki MFC sprawdza przecieków pamięci. W tym momencie wszelkie przecieki pamięci są raportowane za pośrednictwem **debugowania** okna programu Visual Studio.

Gdy aplikacja ładuje innej biblioteki przed biblioteki MFC, niektóre alokacji pamięci w tej bibliotece będzie niepoprawnie raportowane jako przecieków pamięci. Przecieki pamięci false może spowodować aplikację zamknąć powoli, zgodnie z biblioteki MFC raportuje je. W takim przypadku należy użyć `AfxEnableMemoryLeakDump` wyłączyć zrzut przecieku pamięci.

> [!NOTE]
>  Jeśli ta metoda umożliwia wyłączanie zrzut przecieku pamięci, nie otrzymasz raporty przecieki pamięci prawidłowy w aplikacji. Tej metody należy używać tylko w przypadku, gdy masz pewność, że raport przecieku pamięci zawiera przecieki pamięci false.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxenablememorytracking"></a>  Afxenablememorytracking —

Pamięć diagnostycznych śledzenia zwykle jest włączone w wersji debugowania MFC.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Parametry

*bTrack*<br/>
Ustawienie wartości TRUE włącza śledzenie pamięci Wartość FALSE wyłącza je.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienie flagi śledzenia Włącz.

### <a name="remarks"></a>Uwagi

Aby wyłączyć śledzenie na sekcje, w którym wiadomo, że są poprawnie przydzielanie bloków kodu, należy użyć tej funkcji.

Aby uzyskać więcej informacji na temat `AfxEnableMemoryTracking`, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Ta funkcja działa tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxismemoryblock"></a>  Afxismemoryblock —

Sprawdza adres pamięci, aby upewnić się, reprezentuje blok aktualnie aktywnej pamięci, która została przydzielona przez diagnostycznych wersję **nowe**.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskazuje blok pamięci, które ma zostać przetestowana.

*nBytes*<br/>
Zawiera długość bloku pamięci w bajtach.

*plRequestNumber*<br/>
Wskazuje **długie** liczba całkowita, która zostanie wypełniona numer sekwencyjny alokacji bloku pamięci lub zero, jeśli nie reprezentuje blok pamięci aktualnie aktywne.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli przydzielonego bloku pamięci i długość są prawidłowe; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Sprawdza również określony rozmiar względem oryginalnego przydzielony rozmiar. Jeśli funkcja zwraca wartość różną od zera, numer sekwencyjny alokacji jest zwracany w *plRequestNumber*. Ta wartość liczbowa określa kolejność, w którym przydzielono blok względem wszystkich innych **nowe** alokacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxisvalidaddress"></a>  Afxisvalidaddress —

Sprawdza każdy adres pamięci, aby upewnić się, że znajduje się całkowicie w obszarze pamięci programu.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Parametry

*LP*<br/>
Wskazuje adres pamięci, która ma zostać przetestowana.

*nBytes*<br/>
Zawiera liczbę bajtów pamięci do sprawdzenia.

*bReadWrite*<br/>
Określa, czy pamięć jest zarówno do odczytu i zapisu (PRAWDA) lub po prostu odczytu (FALSE).

### <a name="return-value"></a>Wartość zwracana

W kompilacjach do debugowania wartość różną od zera, jeśli block określoną ilość pamięci jest całkowicie zawarty w obszarze pamięci programu; w przeciwnym razie 0.

W kompilacjach nieprzeznaczonych do debugowania Jeśli wartość różną od zera *lp* jest wartość NULL; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Adres nie jest ograniczona do przydzielonej przez bloki **nowe**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxisvalidstring"></a>  Afxisvalidstring —

Funkcja ta jest przydatna w celu ustalenia, czy wskaźnik do ciągu jest prawidłowy.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Wskaźnik do testowania.

*nLength*<br/>
Określa długość ciągu do sprawdzenia, w bajtach. Wartość -1 wskazuje, że będzie ciąg zakończony znakiem null.

### <a name="return-value"></a>Wartość zwracana

W kompilacjach do debugowania wartość różną od zera, jeśli określony wskaźnik wskazuje na ciąg o określonym rozmiarze; w przeciwnym razie 0.

W kompilacjach nieprzeznaczonych do debugowania Jeśli wartość różną od zera *lpsz* jest wartość NULL; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxsetallochook"></a>  AfxSetAllocHook

Ustawia podłączania, umożliwiająca wywołania określonej funkcji, zanim każdy blok pamięci jest przydzielony.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Parametry

*pfnAllocHook*<br/>
Określa nazwę funkcji do wywołania. Zobacz uwagi dla prototypu funkcji alokacji.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli chcesz umożliwić alokacji; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Alokator pamięci debugowania biblioteki klas Microsoft Foundation może wywołać funkcję podłączania zdefiniowanych przez użytkownika umożliwia użytkownikowi monitorowanie alokacji pamięci i kontrolować, czy jest dozwolony przydział. Funkcje punktu zaczepienia alokacji mają pierwowzór w następujący sposób:

**BOOL AFXAPI AllocHook (size_t** `nSize` **, BOOL** `bObject` **długie** `lRequestNumber` **);**

*nSize*<br/>
Rozmiar alokacji pamięci proponowany.

*bPakowarka*<br/>
Wartość TRUE, jeśli alokacja `CObject`-pochodnego obiektu; w przeciwnym razie wartość FALSE.

*lRequestNumber*<br/>
Numer sekwencyjny alokacji pamięci.

Należy pamiętać, że AFXAPI konwencji wywoływania oznacza obiekt wywoływany należy usunąć parametrów ze stosu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxdoforallclasses"></a>  AfxDoForAllClasses

Wywołuje funkcję iteracji dla wszystkich możliwych do serializacji `CObject`-klasy pochodne w przestrzeni pamięci aplikacji.

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*nazwy pfn*<br/>
Wskazuje funkcję iteracji będzie wywoływana dla każdej klasy. Argumenty funkcji są wskaźnik do `CRuntimeClass` obiektu i pusty wskaźnik do dodatkowych danych, które obiekt wywołujący dostarcza do funkcji.

*pContext*<br/>
Wskazuje opcjonalnymi danymi, które obiekt wywołujący może dostarczać funkcji iteracji. This, wskaźnik może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Możliwy do serializacji `CObject`-klas pochodnych są klasy pochodne, za pomocą DECLARE_SERIAL — makro. Wskaźnik, który jest przekazywany do `AfxDoForAllClasses` w *pContext* jest przekazywany do funkcji określonej iteracji za każdym razem jest wywoływana.

> [!NOTE]
>  Ta funkcja działa tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="afxdoforallobjects"></a>  AfxDoForAllObjects

Wykonuje funkcję iteracji, dla wszystkich obiektów pochodną `CObject` przydzielony za pomocą **nowe**.

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*nazwy pfn*<br/>
Wskazuje funkcję iteracji do wykonania dla każdego obiektu. Argumenty funkcji są wskaźnik do `CObject` i wskaźnik typu void dodatkowe dane, który obiekt wywołujący dostarcza do funkcji.

*pContext*<br/>
Wskazuje opcjonalnymi danymi, które obiekt wywołujący może dostarczać funkcji iteracji. This, wskaźnik może mieć wartości NULL.

### <a name="remarks"></a>Uwagi

Stos, globalne, lub obiekty osadzone nie są wyliczane. Wskaźnik przekazywany do `AfxDoForAllObjects` w *pContext* jest przekazywany do funkcji określonej iteracji za każdym razem jest wywoływana.

> [!NOTE]
>  Ta funkcja działa tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
[CObject::Dump](cobject-class.md#dump)
