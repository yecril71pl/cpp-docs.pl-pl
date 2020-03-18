---
title: Usługi diagnostyczne
ms.date: 11/04/2016
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
ms.openlocfilehash: 4cf3f53d1e238218b4eb892dc92e3c823dcc1296
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421402"
---
# <a name="diagnostic-services"></a>Usługi diagnostyczne

Biblioteka MFC dostarcza wiele usług diagnostycznych, które ułatwiają debugowanie programów. Te usługi diagnostyczne obejmują makra i funkcje globalne, które umożliwiają śledzenie alokacji pamięci programu, zrzucanie zawartości obiektów w czasie wykonywania oraz drukowanie komunikatów debugowania w czasie wykonywania. Makra i funkcje globalne dla usług diagnostycznych są pogrupowane w następujące kategorie:

- Ogólne makra diagnostyczne

- Ogólne funkcje diagnostyczne i zmienne

- Funkcje diagnostyczne obiektów

Te makra i funkcje są dostępne dla wszystkich klas pochodzących od `CObject` w debugowaniu i wydaniu wersji MFC. Jednak wszystkie z wyjątkiem DEBUG_NEW i sprawdź, czy w wersji wydanej nic nie rób.

W bibliotece debugowania wszystkie przydzielono bloków pamięci są zamykane z serii "Guard b". Jeśli te bajty są zakłócone przez zapis pamięci errant, procedury diagnostyczne mogą zgłosić problem. Jeśli dołączysz wiersz:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

w pliku implementacji wszystkie wywołania **nowego** będą przechowywać nazwę pliku i numer wiersza, w którym nastąpiło alokacja pamięci. Funkcja [CMemoryState::D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) wyświetli te dodatkowe informacje, co umożliwia zidentyfikowanie przecieków pamięci. Zapoznaj się również z klasą [CDumpContext](../../mfc/reference/cdumpcontext-class.md) , aby uzyskać dodatkowe informacje na temat danych wyjściowych diagnostyki.

Ponadto Biblioteka wykonawcza C obsługuje również zestaw funkcji diagnostycznych, których można użyć do debugowania aplikacji. Aby uzyskać więcej informacji, zobacz [procedury debugowania](../../c-runtime-library/debug-routines.md) w dokumentacji dotyczącej biblioteki wykonawczej.

### <a name="mfc-general-diagnostic-macros"></a>Ogólne makra diagnostyczne MFC

|||
|-|-|
|[STANOWCZ](#assert)|Drukuje komunikat, a następnie przerywa program, jeśli określone wyrażenie zwróci wartość FALSE w debugowanej wersji biblioteki.|
|[ASSERT_KINDOF](#assert_kindof)|Testuje, czy obiekt jest obiektem określonej klasy lub klasą pochodną określonej klasy.|
|[ASSERT_VALID](#assert_valid)|Testuje wewnętrzną ważność obiektu przez wywołanie jego `AssertValid` funkcji członkowskiej; zwykle przesłonięte z `CObject`.|
|[DEBUG_NEW](#debug_new)|Dostarcza nazwę pliku i numer wiersza dla wszystkich alokacji obiektów w trybie debugowania, aby ułatwić znajdowanie przecieków pamięci.|
|[DEBUG_ONLY](#debug_only)|Podobne do ASSERT, ale nie testuje wartości wyrażenia; przydatne dla kodu, który powinien być wykonywany tylko w trybie debugowania.|
|[Upewnij się i ENSURE_VALID](#ensure)|Służy do walidacji poprawności danych.|
|[THIS_FILE](#this_file)|Rozwija do nazwy pliku, który jest kompilowany.|
|[SZUKA](#trace)|Zapewnia możliwości podobne do `printf`w wersji debugowanej biblioteki.|
|[SPRAWDZANIA](#verify)|Podobnie jak w przypadku potwierdzenia, ale szacuje wyrażenie w wersji wydania biblioteki, a także w wersji Debug.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Ogólne zmienne diagnostyczne i funkcje MFC

|||
|-|-|
|[afxDump](#afxdump)|Zmienna globalna, która wysyła informacje [CDumpContext](../../mfc/reference/cdumpcontext-class.md) do okna danych wyjściowych debugera lub do terminalu debugowania.|
|[afxMemDF](#afxmemdf)|Zmienna globalna, która kontroluje zachowanie alokatora pamięci debugowania.|
|[AfxCheckError](#afxcheckerror)|Zmienna globalna służąca do testowania przetestowanej SCODE w celu sprawdzenia, czy jest to błąd, i jeśli tak, zgłasza właściwy błąd.|
|[AfxCheckMemory](#afxcheckmemory)|Sprawdza integralność wszystkich aktualnie przydzieloną pamięci.|
|[AfxDebugBreak](#afxdebugbreak)|Powoduje przerwanie wykonywania.|
|[AfxDump](#cdumpcontext_in_mfc)|Jeśli wywoływana w debugerze, zrzuca stan obiektu podczas debugowania.|
|[AfxDump](#afxdump)|Wewnętrzna funkcja, która zrzuca stan obiektu podczas debugowania.|
|[AfxDumpStack](#afxdumpstack)|Generuj obraz bieżącego stosu. Ta funkcja jest zawsze połączona statycznie.|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|Włącza zrzut przecieku pamięci.|
|[AfxEnableMemoryTracking](#afxenablememorytracking)|Włącza i wyłącza śledzenie pamięci.|
|[AfxIsMemoryBlock](#afxismemoryblock)|Sprawdza, czy blok pamięci został prawidłowo przydzielony.|
|[AfxIsValidAddress](#afxisvalidaddress)|Sprawdza, czy zakres adresów pamięci znajduje się w granicach programu.|
|[AfxIsValidString](#afxisvalidstring)|Określa, czy wskaźnik do ciągu jest prawidłowy.|
|[AfxSetAllocHook](#afxsetallochook)|Włącza wywoływanie funkcji dla każdej alokacji pamięci.|

### <a name="mfc-object-diagnostic-functions"></a>Funkcje diagnostyczne obiektów MFC

|||
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|Wykonuje określoną funkcję we wszystkich klasach pochodnych `CObject`, które obsługują sprawdzanie typu w czasie wykonywania.|
|[AfxDoForAllObjects](#afxdoforallobjects)|Wykonuje określoną funkcję na wszystkich obiektach pochodnych `CObject`, które zostały przydzielono do **nowej**.|

### <a name="mfc-compilation-macros"></a>Makra kompilacji MFC

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Pomija ostrzeżenia kompilatora na potrzeby używania przestarzałych funkcji MFC.|

## <a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

Pomija ostrzeżenia kompilatora na potrzeby używania przestarzałych funkcji MFC.

### <a name="syntax"></a>Składnia

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Przykład

Ten przykładowy kod może spowodować Ostrzeżenie kompilatora, jeśli _AFX_SECURE_NO_WARNINGS nie zostały zdefiniowane.

```cpp
// define this before including any afx files in *pch.h* (*stdafx.h* in Visual Studio 2017 and earlier)
#define _AFX_SECURE_NO_WARNINGS
```
```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a>AfxDebugBreak

Wywołaj tę funkcję, aby spowodować przerwanie (w lokalizacji wywołania `AfxDebugBreak`) podczas wykonywania debugowania wersji aplikacji MFC.

### <a name="syntax"></a>Składnia

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Uwagi

`AfxDebugBreak` nie ma wpływu na wersje wersji aplikacji MFC i należy je usunąć. Ta funkcja powinna być używana tylko w aplikacjach MFC. Użyj Win32 API wersji `DebugBreak`, aby spowodować przerwanie w aplikacjach innych niż MFC.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxver_. h

##  <a name="assert"></a>STANOWCZ

Oblicza jego argument.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Określa wyrażenie (w tym wartości wskaźnika), które ma wartość różną od zera lub 0.

### <a name="remarks"></a>Uwagi

Jeśli wynik wynosi 0, makro drukuje komunikat diagnostyczny i przerywa program. Jeśli warunek jest różny od zera, nic nie robi.

Komunikat diagnostyczny ma postać

`assertion failed in file <name> in line <num>`

gdzie *name* to nazwa pliku źródłowego, a wartość *NUM* to numer wiersza potwierdzenia, który zakończył się niepowodzeniem w pliku źródłowym.

W wydanej wersji MFC, ASSERT nie oblicza wyrażenia i w ten sposób nie przerywa tego programu. Jeśli wyrażenie musi być oceniane niezależnie od środowiska, należy użyć Weryfikuj makro zamiast potwierdzenia.

> [!NOTE]
>  Ta funkcja jest dostępna tylko w wersji debugowanej MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="assert_kindof"></a>ASSERT_KINDOF

To makro potwierdza, że obiekt wskazywany jest obiektem określonej klasy lub jest obiektem klasy pochodzącej od określonej klasy.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Parametry

*nazwą*<br/>
Nazwa klasy pochodnej `CObject`.

*pobject*<br/>
Wskaźnik do obiektu klasy.

### <a name="remarks"></a>Uwagi

Parametr *pObject* powinien być wskaźnikiem do obiektu i może być wartością **stałą**. Obiekt wskazywany i Klasa musi obsługiwać `CObject` informacji o klasie czasu wykonywania. Na przykład, aby upewnić się, że `pDocument` jest wskaźnikiem do obiektu klasy `CMyDoc` lub dowolnymi z jego pochodnych, można kod:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

Użycie makra `ASSERT_KINDOF` jest dokładnie takie samo jak kodowanie:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Ta funkcja działa tylko w przypadku klas zadeklarowanych przy użyciu makra [DECLARE_DYNAMIC] (Run-Time-Object-Model-Services. MD # declare_dynamic lub [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) .

> [!NOTE]
>  Ta funkcja jest dostępna tylko w wersji debugowanej MFC.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="assert_valid"></a>ASSERT_VALID

Służy do testowania założeń o ważności stanu wewnętrznego obiektu.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Parametry

*pObject*<br/>
Określa obiekt klasy pochodnej `CObject`, która ma zastępujące wersję funkcji członkowskiej `AssertValid`.

### <a name="remarks"></a>Uwagi

ASSERT_VALID wywołuje funkcję członkowską `AssertValid` obiektu przekazaną jako jego argument.

W wersji programu MFC ASSERT_VALID nic nie robi. W wersji debugowej weryfikuje wskaźnik, sprawdza pod względem wartości NULL i wywołuje własne funkcje członkowskie `AssertValid` obiektu. Jeśli którykolwiek z tych testów nie powiedzie się, zostanie wyświetlony komunikat o alercie w taki sam sposób jak w przypadku [potwierdzenia](#assert).

> [!NOTE]
>  Ta funkcja jest dostępna tylko w wersji debugowanej MFC.

Aby uzyskać więcej informacji i przykładów, zobacz [debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="debug_new"></a>DEBUG_NEW

Pomaga w znalezieniu przecieków pamięci.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Uwagi

Możesz użyć DEBUG_NEW wszędzie w programie, aby zwykle przydzielić magazyn sterty przy użyciu operatora **New** .

W trybie debugowania (gdy jest zdefiniowany symbol **_DEBUG** ) DEBUG_NEW śledzi nazwę pliku i numer wiersza dla każdego przydzielonego obiektu. Następnie w przypadku używania funkcji [CMemoryState::D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) , każdy obiekt przydzielony za pomocą DEBUG_NEW jest pokazywany z nazwą pliku i numerem wiersza, do którego została przypisana.

Aby użyć DEBUG_NEW, Wstaw następującą dyrektywę do plików źródłowych:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Po wstawieniu tej dyrektywy preprocesor wstawi DEBUG_NEW wszędzie tam, gdzie używasz **nowego**, a MFC wykonuje resztę. Podczas kompilowania wersji programu, DEBUG_NEW jest rozpoznawana jako prosta **Nowa** operacja, a informacje o nazwie pliku i numerze wiersza nie są generowane.

> [!NOTE]
>  W poprzednich wersjach MFC (4,1 i starszych) należy umieścić instrukcję `#define` po wszystkich instrukcjach, które wywołały makra IMPLEMENT_DYNCREATE lub IMPLEMENT_SERIAL. To nie jest już konieczne.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="debug_only"></a>DEBUG_ONLY

W trybie debugowania (gdy jest zdefiniowany symbol **_DEBUG** ), DEBUG_ONLY oblicza jego argument.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Uwagi

W kompilacji wydania DEBUG_ONLY nie oblicza jej argumentu. Jest to przydatne, gdy masz kod, który powinien być wykonywany tylko w kompilacjach debugowania.

Makro DEBUG_ONLY jest równoznaczne z otaczającym *wyrażeniem* z `#ifdef _DEBUG` i `#endif`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

### <a name="ensure"></a>Upewnij się i ENSURE_VALID

Służy do walidacji poprawności danych.

### <a name="syntax"></a>Składnia

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Określa wyrażenie logiczne, które ma zostać przetestowane.

### <a name="remarks"></a>Uwagi

Celem tych makr jest poprawa poprawności parametrów. Makra uniemożliwiają dalsze przetwarzanie nieprawidłowych parametrów w kodzie. W przeciwieństwie do makr ASSERT, upewnij się, że makro zgłasza wyjątek oprócz generowania potwierdzenia.

Makra działają na dwa sposoby zgodnie z konfiguracją projektu. Makra są wywoływane i generują wyjątek, jeśli potwierdzenie nie powiedzie się. W tym celu w konfiguracjach debugowania (to znaczy, gdzie _DEBUG jest zdefiniowana) makra tworzą potwierdzenie i wyjątek w konfiguracjach wydań, makra generują tylko wyjątek (potwierdzenie nie oblicza wyrażenia w konfiguracjach wersji).

Makro ENSURE_ARG zachowuje się jak makro.

ENSURE_VALID wywołuje makro ASSERT_VALID (które ma wpływ tylko na kompilacje debugowania). Ponadto ENSURE_VALID zgłasza wyjątek, jeśli wskaźnik ma wartość NULL. Test NULL jest wykonywany zarówno w konfiguracji debugowania, jak i wydania.

Jeśli którykolwiek z tych testów nie powiedzie się, zostanie wyświetlony komunikat o alercie w taki sam sposób jak w przypadku potwierdzenia. W razie konieczności makro zgłasza wyjątek nieprawidłowego argumentu.
### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="this_file"></a>THIS_FILE

Rozwija do nazwy pliku, który jest kompilowany.

### <a name="syntax"></a>Składnia

```
THIS_FILE
```

### <a name="remarks"></a>Uwagi

Informacje są używane przez ASSERT i WERYFIKUJą makra. Kreator aplikacji i kreatory kodu umieszczają makro w plikach kodu źródłowego, które tworzy.

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

**Nagłówek:** AFX. h

##  <a name="trace"></a>SZUKA

Wysyła określony ciąg do debugera bieżącej aplikacji.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Uwagi

Zobacz [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) , aby uzyskać opis śledzenia. ŚLEDZENIE i ATLTRACE2 mają takie samo zachowanie.

W wersji debugowanej MFC to makro wysyła określony ciąg do debugera bieżącej aplikacji. W kompilacji wydania to makro jest kompilowane do Nothing (w ogóle nie jest generowany żaden kod).

Aby uzyskać więcej informacji, zobacz [debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="verify"></a>SPRAWDZANIA

W wersji debugowanej MFC program oblicza jego argument.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Parametry

*booleanExpression*<br/>
Określa wyrażenie (w tym wartości wskaźnika), które ma wartość różną od zera lub 0.

### <a name="remarks"></a>Uwagi

Jeśli wynik wynosi 0, makro drukuje komunikat diagnostyczny i zatrzymuje program. Jeśli warunek jest różny od zera, nic nie robi.

Komunikat diagnostyczny ma postać

`assertion failed in file <name> in line <num>`

gdzie *name* to nazwa pliku źródłowego, a *NUM* to numer wiersza potwierdzenia, który zakończył się niepowodzeniem w pliku źródłowym.

W wydanej wersji MFC Sprawdź, czy szacuje wyrażenie, ale nie drukuje ani nie przerywa programu. Na przykład jeśli wyrażenie jest wywołaniem funkcji, wywołanie zostanie wykonane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext w MFC)

Zapewnia podstawową możliwość zatopienia obiektów w aplikacji.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Uwagi

`afxDump` to wstępnie zdefiniowany obiekt [CDumpContext](../../mfc/reference/cdumpcontext-class.md) , który umożliwia wysyłanie `CDumpContext` informacji do okna danych wyjściowych debugera lub do terminalu debugowania. Zwykle do `CObject::Dump`należy podać `afxDump` jako parametr.

W systemie Windows NT i wszystkich wersjach systemu Windows, dane wyjściowe `afxDump` są wysyłane do okna debugowania danych wyjściowych C++ wizualizacji podczas debugowania aplikacji.

Ta zmienna jest definiowana tylko w wersji debugowania MFC. Aby uzyskać więcej informacji na temat `afxDump`, zobacz [debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="afxdump"></a>AfxDump (wewnętrzny)

Funkcja wewnętrzna, która używa MFC do zrzutu stanu obiektu podczas debugowania.

### <a name="syntax"></a>Składnia

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Wskaźnik do obiektu klasy pochodzącej od `CObject`.

### <a name="remarks"></a>Uwagi

`AfxDump` wywołuje funkcję elementu członkowskiego `Dump` obiektu i wysyła informacje do lokalizacji określonej przez zmienną `afxDump`. `AfxDump` jest dostępny tylko w debugowanej wersji MFC.

Kod programu nie powinien wywoływać `AfxDump`, ale powinien wywołać `Dump` funkcję członkowską odpowiedniego obiektu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxmemdf"></a>afxMemDF

Ta zmienna jest dostępna z debugera lub programu i umożliwia dostrajanie diagnostyki alokacji.

```
int  afxMemDF;
```

### <a name="remarks"></a>Uwagi

`afxMemDF` mogą mieć następujące wartości określone przez Wyliczenie `afxMemDF`:

- `allocMemDF` włącza funkcję alokatora debugowania (ustawienie domyślne w bibliotece debugowania).

- `delayFreeMemDF` opóźnia zwalnianie pamięci. Gdy program zwalnia blok pamięci, Alokator nie zwraca tej pamięci do podstawowego systemu operacyjnego. Spowoduje to umieszczenie maksymalnego obciążenia pamięci w programie.

- Wywołania `checkAlwaysMemDF` `AfxCheckMemory` za każdym razem, gdy pamięć zostanie przypisana lub zwolniona. Znacznie spowalnia alokacje pamięci i cofa alokacje.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxcheckerror"></a>AfxCheckError

Ta funkcja testuje przekazaną SCODE, aby sprawdzić, czy jest to błąd.

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Uwagi

Jeśli jest to błąd, funkcja zgłasza wyjątek. Jeśli przesłany SCODE jest E_OUTOFMEMORY, funkcja zgłasza [CMemoryException](../../mfc/reference/cmemoryexception-class.md) przez wywołanie [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). W przeciwnym razie funkcja zgłasza [COleException](../../mfc/reference/coleexception-class.md) przez wywołanie [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Ta funkcja może służyć do sprawdzania zwracanych wartości wywołań funkcji OLE w aplikacji. Testując wartość zwracaną z tą funkcją w aplikacji, można prawidłowo reagować na warunki błędów przy minimalnej ilości kodu.

> [!NOTE]
>  Ta funkcja ma ten sam efekt w kompilacjach debugowania i niedebugowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxcheckmemory"></a>AfxCheckMemory

Ta funkcja sprawdza poprawność puli wolnej pamięci i w razie potrzeby drukuje komunikaty o błędach.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli nie występują błędy pamięci; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli funkcja nie wykryje uszkodzenia pamięci, nie drukuje nic.

Wszystkie bloki pamięci aktualnie przydzielone do sterty są sprawdzane, łącznie z tymi przydzielonymi przez **nowe** , ale nie są przydzielone przez bezpośrednie wywołania do przydziałów pamięci, takich jak funkcja **malloc** lub `GlobalAlloc` funkcji systemu Windows. Jeśli dowolna z bloków zostanie uszkodzona, komunikat jest drukowany w danych wyjściowych debugera.

Jeśli dołączysz wiersz

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

w module programu następnie kolejne wywołania `AfxCheckMemory` pokazują nazwę pliku i numer wiersza, do którego została przypisana pamięć.

> [!NOTE]
>  Jeśli moduł zawiera jedną lub więcej implementacji klas, które można serializować, należy umieścić wiersz `#define` po ostatnim IMPLEMENT_SERIAL wywołaniu makra.

Ta funkcja działa tylko w wersji debugowanej MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxdump"></a>AfxDump (MFC)

Wywołaj tę funkcję w debugerze, aby zrzucić stan obiektu podczas debugowania.

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Wskaźnik do obiektu klasy pochodzącej od `CObject`.

### <a name="remarks"></a>Uwagi

`AfxDump` wywołuje funkcję elementu członkowskiego `Dump` obiektu i wysyła informacje do lokalizacji określonej przez zmienną `afxDump`. `AfxDump` jest dostępny tylko w debugowanej wersji MFC.

Kod programu nie powinien wywoływać `AfxDump`, ale powinien wywołać `Dump` funkcję członkowską odpowiedniego obiektu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxdumpstack"></a>AfxDumpStack

Ta funkcja globalna może służyć do generowania obrazu bieżącego stosu.

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Parametry

*dwTarget*<br/>
Wskazuje element docelowy zrzutu danych wyjściowych. Możliwe wartości, które można łączyć za pomocą operatora bitowego lub ( **&#124;** ), są następujące:

- AFX_STACK_DUMP_TARGET_TRACE wysyła dane wyjściowe przy użyciu makra [śledzenia](#trace) . Makro śledzenia generuje dane wyjściowe tylko w kompilacjach debugowania. nie generuje danych wyjściowych w kompilacjach wydania. Ponadto śledzenie można przekierować do innych obiektów docelowych poza debugerem.

- AFX_STACK_DUMP_TARGET_DEFAULT wysyła dane wyjściowe zrzutu do domyślnego obiektu docelowego. W przypadku kompilacji debugowania dane wyjściowe są przekazywane do makra śledzenia. W kompilacji wydania dane wyjściowe trafiają do Schowka.

- AFX_STACK_DUMP_TARGET_CLIPBOARD wysyła dane wyjściowe tylko do Schowka. Dane są umieszczane w schowku jako zwykły tekst przy użyciu formatu Schowka CF_TEXT.

- AFX_STACK_DUMP_TARGET_BOTH wysyła dane wyjściowe do schowka i makro śledzenia jednocześnie.

- AFX_STACK_DUMP_TARGET_ODS wysyła dane wyjściowe bezpośrednio do debugera za pomocą funkcji Win32 `OutputDebugString()`. Ta opcja spowoduje wygenerowanie danych wyjściowych debugera w kompilacjach i wersjach, gdy debuger zostanie dołączony do procesu. AFX_STACK_DUMP_TARGET_ODS zawsze osiągnie debuger (jeśli jest dołączony) i nie może zostać przekierowany.

### <a name="remarks"></a>Uwagi

W poniższym przykładzie przedstawiono pojedynczy wiersz danych wyjściowych generowanych z wywoływania `AfxDumpStack` z procedury obsługi przycisku w aplikacji okna dialogowego MFC:

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

Każdy wiersz w danych wyjściowych jest określany jako adres ostatniego wywołania funkcji, pełna nazwa ścieżki modułu zawierającego wywołanie funkcji i prototyp funkcji o nazwie. Jeśli wywołanie funkcji na stosie nie nastąpi przy dokładnym adresie funkcji, wyświetlane jest przesunięcie bajtów.

Na przykład poniższa tabela opisuje pierwszy wiersz powyższych danych wyjściowych:

|Dane wyjściowe|Opis|
|------------|-----------------|
|`00427D55:`|Adres zwrotny ostatniego wywołania funkcji.|
|`DUMP2\DEBUG\DUMP2.EXE!`|Pełna nazwa ścieżki modułu zawierającego wywołanie funkcji.|
|`void AfxDumpStack(unsigned long)`|Prototyp funkcji o nazwie.|
|`+ 181 bytes`|Przesunięcie w bajtach od adresu prototypu funkcji (w tym przypadku `void AfxDumpStack(unsigned long)`) na adres zwrotny (w tym przypadku `00427D55`).|

`AfxDumpStack` jest dostępna w debugowaniu i niedebugowanych wersjach bibliotek MFC; Jednak funkcja jest zawsze połączona statycznie, nawet jeśli plik wykonywalny używa MFC w udostępnionej bibliotece DLL. W implementacjach biblioteki udostępnionej funkcja znajduje się w MFCS42. Biblioteka LIB (i jej warianty).

Aby użyć tej funkcji pomyślnie:

- Plik IMAGEHLP. Biblioteka DLL musi znajdować się w ścieżce. Jeśli nie masz tej biblioteki DLL, funkcja wyświetli komunikat o błędzie. Zobacz [Biblioteka pomocy obrazów](/windows/win32/Debug/image-help-library) , aby uzyskać informacje o zestawie funkcji dostarczonym przez program Imagehlp.

- Moduły z ramkami na stosie muszą zawierać informacje o debugowaniu. Jeśli nie zawierają one informacji debugowania, funkcja nadal generuje ślad stosu, ale ślad będzie mniej szczegółowy.
  ### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump

Włącza i wyłącza zrzut przecieku pamięci w destruktorze AFX_DEBUG_STATE.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Parametry

*bDump*<br/>
podczas Wartość TRUE wskazuje, że zrzut przecieku pamięci jest włączony; Wartość FALSE wskazuje, że zrzut przecieku pamięci jest wyłączony.

### <a name="return-value"></a>Wartość zwrócona

Poprzednia wartość dla tej flagi.

### <a name="remarks"></a>Uwagi

Gdy aplikacja zwalnia bibliotekę MFC, biblioteka MFC sprawdza przecieki pamięci. W tym momencie wszelkie przecieki pamięci są raportowane użytkownikowi za pomocą okna **debugowania** programu Visual Studio.

Jeśli aplikacja ładuje inną bibliotekę przed biblioteką MFC, niektóre alokacje pamięci w tej bibliotece zostaną nieprawidłowo zgłoszone jako przecieki pamięci. Fałszywe przecieki pamięci mogą spowodować spowolnienie działania aplikacji, gdy biblioteka MFC zgłosi te problemy. W takim przypadku należy użyć `AfxEnableMemoryLeakDump`, aby wyłączyć zrzut przecieków pamięci.

> [!NOTE]
>  W przypadku użycia tej metody w celu wyłączenia zrzutu przecieków pamięci nie będą wyświetlane raporty dotyczące prawidłowych przecieków pamięci w aplikacji. Tej metody należy użyć tylko wtedy, gdy masz pewność, że raport o przecieku pamięci zawiera fałszywe przecieki pamięci.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxenablememorytracking"></a>AfxEnableMemoryTracking

Śledzenie pamięci diagnostycznej jest zwykle włączone w wersji debugowania MFC.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Parametry

*bTrack*<br/>
Ustawienie tej wartości na TRUE powoduje włączenie śledzenia pamięci; Wartość FALSE powoduje wyłączenie tej opcji.

### <a name="return-value"></a>Wartość zwrócona

Poprzednie ustawienie flagi śledzenie — włączenie.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby wyłączyć śledzenie dla sekcji kodu, o którym wiadomo, że bloki są przydzielane poprawnie.

Aby uzyskać więcej informacji na temat `AfxEnableMemoryTracking`, zobacz [debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Ta funkcja działa tylko w wersji debugowanej MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxismemoryblock"></a>AfxIsMemoryBlock

Testuje adres pamięci, aby upewnić się, że reprezentuje aktualnie aktywny blok pamięci, który został przydzielony przez wersję diagnostyczną **nowej**.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Parametry

*St*<br/>
Wskazuje blok pamięci do przetestowania.

*nBytes*<br/>
Zawiera długość bloku pamięci w bajtach.

*plRequestNumber*<br/>
Wskazuje **długą** liczbę całkowitą, która zostanie wypełniona z numerem sekwencji alokacji bloku pamięci lub zero, jeśli nie reprezentuje aktualnie aktywnego bloku pamięci.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli blok pamięci jest aktualnie przydzielony i długość jest poprawna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Sprawdza również określony rozmiar względem oryginalnego przyznanego rozmiaru. Jeśli funkcja zwraca wartość różną od zera, numer sekwencji alokacji jest zwracany w *plRequestNumber*. Ta liczba reprezentuje kolejność, w której został przydzielony blok względem wszystkich innych **nowych** alokacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxisvalidaddress"></a>AfxIsValidAddress

Testuje dowolny adres pamięci, aby upewnić się, że jest on zawarty w całości w przestrzeni pamięci programu.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Parametry

*LP*<br/>
Wskazuje adres pamięci do przetestowania.

*nBytes*<br/>
Zawiera liczbę bajtów pamięci do przetestowania.

*bReadWrite*<br/>
Określa, czy pamięć jest zarówno do odczytu, jak i do zapisu (TRUE), czy tylko do odczytu (FALSE).

### <a name="return-value"></a>Wartość zwrócona

W przypadku kompilacji debugowania, jeśli określony blok pamięci jest zawarty w całości w przestrzeni pamięci programu; w przeciwnym razie 0.

W kompilacjach niezwiązanych z debugowaniem niezerowe, jeśli *LP* nie ma wartości null; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Adres nie jest ograniczony do bloków przyznanych przez **Nowy**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxisvalidstring"></a>AfxIsValidString

Użyj tej funkcji, aby określić, czy wskaźnik do ciągu jest prawidłowy.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Wskaźnik do przetestowania.

*nLength*<br/>
Określa długość ciągu do przetestowania, w bajtach. Wartość-1 oznacza, że ciąg będzie zakończony znakiem null.

### <a name="return-value"></a>Wartość zwrócona

W kompilacjach debugowania, wartość niezerowa, jeśli określony wskaźnik wskazuje na ciąg o określonym rozmiarze; w przeciwnym razie 0.

W kompilacjach niezwiązanych z debugowaniem niezerowe, jeśli *lpsz* nie ma wartości null; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxsetallochook"></a>AfxSetAllocHook

Ustawia element Hook, który umożliwia wywołanie określonej funkcji przed przydzieleniem bloku pamięci.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Parametry

*pfnAllocHook*<br/>
Określa nazwę funkcji do wywołania. Zapoznaj się z uwagami dotyczącymi prototypu funkcji alokacji.

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli chcesz zezwolić na alokację; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Program przydzielający pamięć biblioteka MFC może wywołać funkcję podłączania zdefiniowane przez użytkownika, aby umożliwić użytkownikowi monitorowanie alokacji pamięci i określanie, czy alokacja jest dozwolona. Funkcje punktu zaczepienia alokacji są prototypami w następujący sposób:

**Bool AFXAPI AllocHook (size_t** `nSize` **, bool** `bObject` **, Long** `lRequestNumber` **);**

*nSize*<br/>
Rozmiar proponowanej alokacji pamięci.

*bObject*<br/>
Ma wartość TRUE, jeśli alokacja dotyczy obiektu pochodnego `CObject`; w przeciwnym razie FALSE.

*lRequestNumber*<br/>
Numer sekwencyjny alokacji pamięci.

Należy zauważyć, że Konwencja wywoływania AFXAPI oznacza, że obiekt wywołujący musi usunąć parametry ze stosu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxdoforallclasses"></a>AfxDoForAllClasses

Wywołuje określoną funkcję iteracji dla wszystkich możliwych do serializacji klas pochodnych `CObject`w przestrzeni pamięci aplikacji.

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*PFN*<br/>
Wskazuje funkcję iteracji, która ma zostać wywołana dla każdej klasy. Argumenty funkcji są wskaźnikiem do obiektu `CRuntimeClass` i pustym wskaźnikiem do dodatkowych danych, które obiekt wywołujący dostarcza do funkcji.

*pContext*<br/>
Wskazuje opcjonalne dane, które obiekt wywołujący może dostarczyć funkcji iteracji. Ten wskaźnik może mieć wartość NULL.

### <a name="remarks"></a>Uwagi

Możliwe do serializacji klasy pochodne `CObject`są klasy pochodne przy użyciu makra DECLARE_SERIAL. Wskaźnik, który jest przesyłany do `AfxDoForAllClasses` w *pContext* , jest przenoszona do określonej funkcji iteracji przy każdym wywołaniu.

> [!NOTE]
>  Ta funkcja działa tylko w wersji debugowanej MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="afxdoforallobjects"></a>AfxDoForAllObjects

Wykonuje określoną funkcję iteracji dla wszystkich obiektów pochodnych `CObject`, które zostały przydzielono do **nowej**.

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*PFN*<br/>
Wskazuje funkcję iteracji do wykonania dla każdego obiektu. Argumenty funkcji są wskaźnikiem do `CObject` i pustym wskaźnikiem do dodatkowych danych, które obiekt wywołujący dostarcza do funkcji.

*pContext*<br/>
Wskazuje opcjonalne dane, które obiekt wywołujący może dostarczyć funkcji iteracji. Ten wskaźnik może mieć wartość NULL.

### <a name="remarks"></a>Uwagi

Obiekty stosu, globalne lub osadzone nie są wyliczane. Wskaźnik przesłany do `AfxDoForAllObjects` w *pContext* jest przenoszona do określonej funkcji iteracji przy każdym wywołaniu.

> [!NOTE]
>  Ta funkcja działa tylko w wersji debugowanej MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra i Globals](mfc-macros-and-globals.md)<br/>
[CObject::D UMP](cobject-class.md#dump)
