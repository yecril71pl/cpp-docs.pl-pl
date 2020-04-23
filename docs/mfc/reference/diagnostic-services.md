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
ms.openlocfilehash: f952044f4320aea1a757559b3c9c51e8ffb7c3a6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751646"
---
# <a name="diagnostic-services"></a>Usługi diagnostyczne

Biblioteka klas Programu Microsoft Foundation dostarcza wiele usług diagnostycznych, które ułatwiają debugowanie programów. Te usługi diagnostyczne obejmują makra i funkcje globalne, które umożliwiają śledzenie alokacji pamięci programu, zrzutu zawartości obiektów w czasie wykonywania i drukowania komunikatów debugowania w czasie wykonywania. Makra i funkcje globalne dla usług diagnostycznych są pogrupowane w następujące kategorie:

- Ogólne makra diagnostyczne

- Ogólne funkcje diagnostyczne i zmienne

- Funkcje diagnostyki obiektów

Te makra i funkcje są dostępne `CObject` dla wszystkich klas pochodzących z wersji debugowania i wydania MFC. Jednak wszystkie z wyjątkiem DEBUG_NEW i VERIFY nic nie robią w wersji release.

W bibliotece debugowania wszystkie przydzielone bloki pamięci są otoczone szeregiem "bajtów straży". Jeśli te bajty są zakłócane przez błąd zapis pamięci, procedury diagnostyczne mogą zgłosić problem. Jeśli uwzględnisz wiersz:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

w pliku implementacji wszystkie wywołania **new** będą przechowywane numer pliku i wiersza, w którym miała miejsce alokacja pamięci. Funkcja [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) wyświetli te dodatkowe informacje, co pozwala zidentyfikować przecieki pamięci. Zapoznaj się również z klasy [CDumpContext](../../mfc/reference/cdumpcontext-class.md) dodatkowe informacje na temat danych wyjściowych diagnostycznych.

Ponadto biblioteka w czasie wykonywania języka C obsługuje również zestaw funkcji diagnostycznych, których można użyć do debugowania aplikacji. Aby uzyskać więcej informacji, zobacz [procedury debugowania](../../c-runtime-library/debug-routines.md) w odwołaniu do biblioteki w czasie wykonywania.

### <a name="mfc-general-diagnostic-macros"></a>Ogólne makra diagnostyczne MFC

|||
|-|-|
|[Assert](#assert)|Drukuje wiadomość, a następnie przerywa program, jeśli określone wyrażenie ma wartość FALSE w wersji debugowania biblioteki.|
|[ASSERT_KINDOF](#assert_kindof)|Sprawdza, czy obiekt jest obiektem określonej klasy lub klasy pochodnej określonej klasy.|
|[ASSERT_VALID](#assert_valid)|Testuje ważność wewnętrzną obiektu, `AssertValid` wywołując jego funkcję elementu członkowskiego; zazwyczaj zastępowane z `CObject`.|
|[Debug_new](#debug_new)|Dostarcza nazwę pliku i numer wiersza dla wszystkich alokacji obiektów w trybie debugowania, aby ułatwić znajdowanie przecieków pamięci.|
|[DEBUG_ONLY](#debug_only)|Podobne do ASSERT, ale nie testuje wartość wyrażenia; przydatne dla kodu, który powinien być wykonywany tylko w trybie debugowania.|
|[ZAPEWNIENIE i ENSURE_VALID](#ensure)|Służy do sprawdzania poprawności danych.|
|[THIS_FILE](#this_file)|Rozwija się do nazwy pliku, który jest kompilowany.|
|[Śledzenia](#trace)|Zapewnia `printf`-like możliwości w wersji debugowania biblioteki.|
|[Sprawdź](#verify)|Podobnie jak ASSERT, ale ocenia wyrażenie w wersji wydania biblioteki, jak również w wersji debugowania.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Ogólne zmienne diagnostyczne i funkcje MFC

|||
|-|-|
|[afxDump (właśc.](#afxdump)|Zmienna globalna, która wysyła informacje [CDumpContext](../../mfc/reference/cdumpcontext-class.md) do okna wyjściowego debugera lub do terminalu debugowania.|
|[Afxmemdf](#afxmemdf)|Zmienna globalna, która kontroluje zachowanie alokatora pamięci debugowania.|
|[AfxCheckError](#afxcheckerror)|Zmienna globalna używana do testowania przekazanych kodów SCODE, aby sprawdzić, czy jest to błąd, a jeśli tak, zgłasza odpowiedni błąd.|
|[AfxCheckMemory (AfxCheckMemory)](#afxcheckmemory)|Sprawdza integralność wszystkich aktualnie przydzielonych pamięci.|
|[AfxDebugBreak (AfxDebugBreak)](#afxdebugbreak)|Powoduje przerwę w wykonywaniu.|
|[AfxDump ( AfxDump )](#cdumpcontext_in_mfc)|Jeśli wywoływane w debugerze, zrzuca stan obiektu podczas debugowania.|
|[AfxDump ( AfxDump )](#afxdump)|Funkcja wewnętrzna, która zrzuca stan obiektu podczas debugowania.|
|[AfxDumpStack (AfxDumpStack)](#afxdumpstack)|Generowanie obrazu bieżącego stosu. Ta funkcja jest zawsze połączona statycznie.|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|Włącza zrzut przecieku pamięci.|
|[AfxEnableMemoryTracking (Śledzenie)](#afxenablememorytracking)|Włącza i wyłącza śledzenie pamięci.|
|[AfxIsMemoryBlock](#afxismemoryblock)|Sprawdza, czy blok pamięci został prawidłowo przydzielony.|
|[AfxIsValidAddress](#afxisvalidaddress)|Sprawdza, czy zakres adresów pamięci mieści się w granicach programu.|
|[AfxIsValidString (AfxIsValidString)](#afxisvalidstring)|Określa, czy wskaźnik do ciągu jest prawidłowy.|
|[AfxSetAllocHook (AfxSetAllocHook)](#afxsetallochook)|Włącza wywołanie funkcji w każdej alokacji pamięci.|

### <a name="mfc-object-diagnostic-functions"></a>Funkcje diagnostyczne obiektów MFC

|||
|-|-|
|[AfxDoForAllClasses (Klasy AfxDoForAll)](#afxdoforallclasses)|Wykonuje określoną funkcję `CObject`we wszystkich klasach pochodnych, które obsługują sprawdzanie typu w czasie wykonywania.|
|[AfxDoForAllObjects afxdoforallobjects AfxDoForAllObjects Afx](#afxdoforallobjects)|Wykonuje określoną funkcję `CObject`dla wszystkich obiektów pochodnych, które zostały przydzielone **nowym**.|

### <a name="mfc-compilation-macros"></a>Makra kompilacji MFC

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Pomija ostrzeżenia kompilatora dla korzystania z przestarzałych funkcji MFC.|

## <a name="_afx_secure_no_warnings"></a><a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

Pomija ostrzeżenia kompilatora dla korzystania z przestarzałych funkcji MFC.

### <a name="syntax"></a>Składnia

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Przykład

Ten przykładowy kod spowoduje ostrzeżenie kompilatora, jeśli nie zostały zdefiniowane _AFX_SECURE_NO_WARNINGS.

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

## <a name="afxdebugbreak"></a><a name="afxdebugbreak"></a>AfxDebugBreak (AfxDebugBreak)

Wywołanie tej funkcji, aby spowodować przerwę `AfxDebugBreak`(w lokalizacji wywołania do) w wykonaniu wersji debugowania aplikacji MFC.

### <a name="syntax"></a>Składnia

```cpp
void AfxDebugBreak( );
```

### <a name="remarks"></a>Uwagi

`AfxDebugBreak`nie ma wpływu w wersjach wydania aplikacji MFC i powinny zostać usunięte. Ta funkcja powinna być używana tylko w aplikacjach MFC. Użyj wersji interfejsu API `DebugBreak`Win32, aby spowodować przerwę w aplikacjach innych niż MFC.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxver_.h

## <a name="assert"></a><a name="assert"></a>Assert

Ocenia jego argument.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Parametry

*booleanWyrażenie*<br/>
Określa wyrażenie (w tym wartości wskaźnika), które jest obliczane na wartość niezerową lub 0.

### <a name="remarks"></a>Uwagi

Jeśli wynik wynosi 0, makro drukuje komunikat diagnostyczny i przerywa program. Jeśli warunek jest niezerowy, nic nie robi.

Komunikat diagnostyczny ma formularz

`assertion failed in file <name> in line <num>`

gdzie *nazwa* jest nazwą pliku źródłowego, a *numer jest* numerem wiersza potwierdzenia, które nie powiodło się w pliku źródłowym.

W wersji MFC ASSERT nie ocenia wyrażenia i w związku z tym nie przerywa programu. Jeśli wyrażenie musi być oceniane niezależnie od środowiska, należy użyć weryfikuj makro zamiast ASSERT.

> [!NOTE]
> Ta funkcja jest dostępna tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="assert_kindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF

To makro twierdzi, że obiekt wskazał jest obiektem określonej klasy lub jest obiektem klasy pochodną określonej klasy.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Parametry

*Classname*<br/>
Nazwa klasy `CObject`pochodnej.

*Pobject*<br/>
Wskaźnik do obiektu klasy.

### <a name="remarks"></a>Uwagi

Parametr *pobject* powinien być wskaźnikiem do obiektu i może być **const**. Obiekt wskazywki i `CObject` klasy musi obsługiwać informacje o klasie w czasie wykonywania. Na przykład, aby `pDocument` upewnić się, że `CMyDoc` jest wskaźnikiem do obiektu klasy lub któregokolwiek z jego pochodnych, można kodować:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

Korzystanie `ASSERT_KINDOF` z makra jest dokładnie takie samo jak kodowanie:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Ta funkcja działa tylko dla klas zadeklarowanych za pomocą makra [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic lub [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) makra.

> [!NOTE]
> Ta funkcja jest dostępna tylko w wersji debugowania MFC.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="assert_valid"></a><a name="assert_valid"></a>ASSERT_VALID

Służy do testowania założeń dotyczących ważności stanu wewnętrznego obiektu.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Parametry

*Pobject*<br/>
Określa obiekt klasy pochodnej, `CObject` która ma nadrzędną wersję `AssertValid` funkcji elementu członkowskiego.

### <a name="remarks"></a>Uwagi

ASSERT_VALID wywołuje funkcję `AssertValid` elementu członkowskiego obiektu przekazany jako jego argument.

W wersji MFC ASSERT_VALID nic nie robi. W wersji debugowania sprawdza poprawność wskaźnika, sprawdza wartość NULL `AssertValid` i wywołuje funkcje własne gołąb. Jeśli którykolwiek z tych testów zakończy się niepowodzeniem, komunikat alertu jest wyświetlany w taki sam sposób jak [ASSERT](#assert).

> [!NOTE]
> Ta funkcja jest dostępna tylko w wersji debugowania MFC.

Aby uzyskać więcej informacji i przykładów, zobacz [Debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="debug_new"></a><a name="debug_new"></a>Debug_new

Pomaga w znalezieniu przecieków pamięci.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Uwagi

Można użyć DEBUG_NEW wszędzie w programie, które zwykle używają **nowego** operatora do przydzielania magazynu sterty.

W trybie debugowania (po zdefiniowaniu symbolu **_DEBUG)** DEBUG_NEW śledzi nazwę pliku i numer wiersza dla każdego obiektu, który przydziela. Następnie podczas korzystania z funkcji elementu członkowskiego [CMemoryState::DumpAllObjects,](cmemorystate-structure.md#dumpallobjectssince) każdy obiekt przydzielony z DEBUG_NEW jest wyświetlany z numerem pliku i numerem wiersza, w którym został przydzielony.

Aby użyć DEBUG_NEW, wstaw następującą dyrektywę do plików źródłowych:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Po wstawieniu tej dyrektywy preprocesor wstawi DEBUG_NEW wszędzie tam, gdzie używasz **nowych**, a MFC robi resztę. Podczas kompilowania wersji programu DEBUG_NEW jest rozpoznawany na prostą **nową** operację, a informacje o numerze pliku i numerze wiersza nie są generowane.

> [!NOTE]
> W poprzednich wersjach MFC (4.1 i wcześniejszych) trzeba było umieścić `#define` instrukcję po wszystkich instrukcji, które nazywa IMPLEMENT_DYNCREATE lub IMPLEMENT_SERIAL makr. Nie jest to już konieczne.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="debug_only"></a><a name="debug_only"></a>DEBUG_ONLY

W trybie debugowania (po zdefiniowaniu symbolu **_DEBUG)** DEBUG_ONLY ocenia jego argument.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Uwagi

W kompilacji wydania DEBUG_ONLY nie ocenia jego argumentu. Jest to przydatne, gdy masz kod, który powinien być wykonywany tylko w kompilacjach debugowania.

Makro DEBUG_ONLY jest równoważne otaczającemu `#ifdef _DEBUG` *wyrazowi* z i . `#endif`

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

### <a name="ensure-and-ensure_valid"></a><a name="ensure"></a>ZAPEWNIENIE i ENSURE_VALID

Służy do sprawdzania poprawności danych.

### <a name="syntax"></a>Składnia

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Parametry

*booleanWyrażenie*<br/>
Określa wyrażenie logiczne, które ma zostać przetestowane.

### <a name="remarks"></a>Uwagi

Celem tych makr jest poprawa walidacji parametrów. Makra uniemożliwiają dalsze przetwarzanie niepoprawnych parametrów w kodzie. W przeciwieństwie do makr ASSERT, UPEWNIJ makra zgłosić wyjątek oprócz generowania potwierdzenia.

Makra zachowują się na dwa sposoby, zgodnie z konfiguracją projektu. Makra wywołać ASSERT, a następnie zgłosić wyjątek, jeśli twierdzenie nie powiedzie się. W związku z tym w konfiguracjach debugowania (czyli gdzie jest zdefiniowana _DEBUG) makra wytwarzają asercja i wyjątek w konfiguracjach wydania, makra generują tylko wyjątek (ASSERT nie ocenia wyrażenia w konfiguracjach wydania).

Makro ENSURE_ARG działa jak makro ENSURE.

ENSURE_VALID wywołuje makro ASSERT_VALID (które ma wpływ tylko w kompilacjach debugowania). Ponadto ENSURE_VALID zgłasza wyjątek, jeśli wskaźnik jest NULL. Test NULL jest wykonywany zarówno w konfiguracjach debugowania, jak i wersji.

Jeśli którykolwiek z tych testów zakończy się niepowodzeniem, komunikat alertu jest wyświetlany w taki sam sposób jak ASSERT. Makro zgłasza wyjątek nieprawidłowego argumentu, jeśli to konieczne.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="this_file"></a><a name="this_file"></a>THIS_FILE

Rozwija się do nazwy pliku, który jest kompilowany.

### <a name="syntax"></a>Składnia

```
THIS_FILE
```

### <a name="remarks"></a>Uwagi

Informacje są używane przez makra ASSERT i VERIFY. Kreator aplikacji i kreatory kodu umieszczają makro w utworzonych przez nie plikach kodu źródłowego.

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

## <a name="trace"></a><a name="trace"></a>Śledzenia

Wysyła określony ciąg do debugera bieżącej aplikacji.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Uwagi

Opis śledzenia można znaleźć w [części ATLTRACE2.](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) TRACE i ATLTRACE2 mają takie samo zachowanie.

W wersji debugowania MFC to makro wysyła określony ciąg do debugera bieżącej aplikacji. W kompilacji wydania to makro kompiluje się do niczego (żaden kod nie jest generowany).

Aby uzyskać więcej informacji, zobacz [Debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="verify"></a><a name="verify"></a>Sprawdź

W wersji debugowania MFC, ocenia jego argument.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Parametry

*booleanWyrażenie*<br/>
Określa wyrażenie (w tym wartości wskaźnika), które jest obliczane na wartość niezerową lub 0.

### <a name="remarks"></a>Uwagi

Jeśli wynik wynosi 0, makro drukuje komunikat diagnostyczny i zatrzymuje program. Jeśli warunek jest niezerowy, nic nie robi.

Komunikat diagnostyczny ma formularz

`assertion failed in file <name> in line <num>`

gdzie *nazwa* jest nazwą pliku źródłowego i *numer jest* numer wiersza potwierdzenia, które nie powiodło się w pliku źródłowym.

W wersji wydania MFC, VERIFY ocenia wyrażenie, ale nie drukuje ani nie przerywa programu. Na przykład jeśli wyrażenie jest wywołaniem funkcji, zostanie wykonane wywołanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext w MFC)

Zapewnia podstawowe możliwości zatapiania obiektów w aplikacji.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Uwagi

`afxDump`jest wstępnie zdefiniowanym obiektem [CDumpContext,](../../mfc/reference/cdumpcontext-class.md) `CDumpContext` który umożliwia wysyłanie informacji do okna wyjściowego debugera lub do terminalu debugowania. Zazwyczaj należy podać `afxDump` jako parametr `CObject::Dump`do .

W systemie Windows NT i `afxDump` wszystkich wersjach systemu Windows dane wyjściowe są wysyłane do okna wyjściowego debugowania języka Visual C++ podczas debugowania aplikacji.

Ta zmienna jest zdefiniowana tylko w wersji debugowania MFC. Aby uzyskać `afxDump`więcej informacji na temat , zobacz [Debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxdump-internal"></a><a name="afxdump"></a>AfxDump (wewnętrzny)

Funkcja wewnętrzna, której MFC używa do zrzutu stanu obiektu podczas debugowania.

### <a name="syntax"></a>Składnia

```cpp
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*Pob*<br/>
Wskaźnik do obiektu klasy pochodnej `CObject`.

### <a name="remarks"></a>Uwagi

`AfxDump`wywołuje funkcję `Dump` elementu członkowskiego obiektu i wysyła informacje do `afxDump` lokalizacji określonej przez zmienną. `AfxDump`jest dostępna tylko w wersji debugowania MFC.

Kod programu nie `AfxDump`powinien wywoływać , `Dump` ale zamiast tego należy wywołać funkcję elementu członkowskiego odpowiedniego obiektu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxmemdf"></a><a name="afxmemdf"></a>Afxmemdf

Ta zmienna jest dostępna z debugera lub programu i umożliwia dostosowanie diagnostyki alokacji.

```
int  afxMemDF;
```

### <a name="remarks"></a>Uwagi

`afxMemDF`może mieć następujące wartości określone w wyliczeniu: `afxMemDF`

- `allocMemDF`Włącza debugowanie alokatora (ustawienie domyślne w bibliotece debugowania).

- `delayFreeMemDF`Opóźnia zwalnianie pamięci. Podczas gdy program zwalnia blok pamięci, alokator nie zwraca tej pamięci do podstawowego systemu operacyjnego. Spowoduje to maksymalne obciążenie pamięcią w programie.

- `checkAlwaysMemDF`Wywołania `AfxCheckMemory` za każdym razem, gdy pamięć jest przydzielana lub zwalniana. Spowoduje to znaczne spowolnienie alokacji pamięci i alokacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheckError

Ta funkcja testuje przeszedł SCODE, aby sprawdzić, czy jest to błąd.

```cpp
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Uwagi

Jeśli jest to błąd, funkcja zgłasza wyjątek. Jeśli przekazany SCODE jest E_OUTOFMEMORY, funkcja rzuca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) wywołując [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). W przeciwnym razie funkcja rzuca [COleException](../../mfc/reference/coleexception-class.md) wywołując [AfxThrowOleException](exception-processing.md#afxthrowoleexception).

Ta funkcja może służyć do sprawdzania wartości zwracanych wywołań funkcji OLE w aplikacji. Testując wartość zwracaną za pomocą tej funkcji w aplikacji, można poprawnie reagować na warunki błędu przy minimalnej ilości kodu.

> [!NOTE]
> Ta funkcja ma taki sam efekt w kompilacjach debugowania i bez debugowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxcheckmemory"></a><a name="afxcheckmemory"></a>AfxCheckMemory (AfxCheckMemory)

Ta funkcja sprawdza poprawność puli wolnych pamięci i drukuje komunikaty o błędach zgodnie z wymaganiami.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli nie ma błędów pamięci; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli funkcja nie wykryje uszkodzenia pamięci, nic nie drukuje.

Sprawdzane są wszystkie bloki pamięci aktualnie przydzielone na stercie, w tym bloki przydzielone przez **nowe,** ale nie przydzielone przez bezpośrednie wywołania do podstawowych alokatorów pamięci, takich jak funkcja **malloc** lub funkcja `GlobalAlloc` systemu Windows. Jeśli zostanie znaleziony uszkodzony dowolny blok, wiadomość jest drukowana na wyjściu debugera.

Jeśli uwzględnisz linię

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

w module programu, a `AfxCheckMemory` następnie kolejne wywołania, aby wyświetlić nazwę pliku i numer wiersza, w którym przydzielono pamięć.

> [!NOTE]
> Jeśli moduł zawiera jedną lub więcej implementacji klasy serializable, a następnie należy umieścić `#define` wiersz po ostatnim wywołaniu makra IMPLEMENT_SERIAL.

Ta funkcja działa tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxdump-mfc"></a><a name="afxdump"></a>AfxDump (MFC)

Wywołanie tej funkcji w debugerze, aby zrzucić stan obiektu podczas debugowania.

```cpp
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*Pob*<br/>
Wskaźnik do obiektu klasy pochodnej `CObject`.

### <a name="remarks"></a>Uwagi

`AfxDump`wywołuje funkcję `Dump` elementu członkowskiego obiektu i wysyła informacje do `afxDump` lokalizacji określonej przez zmienną. `AfxDump`jest dostępna tylko w wersji debugowania MFC.

Kod programu nie `AfxDump`powinien wywoływać , `Dump` ale zamiast tego należy wywołać funkcję elementu członkowskiego odpowiedniego obiektu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack (AfxDumpStack)

Ta funkcja globalna może służyć do generowania obrazu bieżącego stosu.

```cpp
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Parametry

*dwTarget*<br/>
Wskazuje miejsce docelowe danych wyjściowych zrzutu. Możliwe wartości, które można łączyć za pomocą operatora bitowego OR **(&#124;) **są następujące:

- AFX_STACK_DUMP_TARGET_TRACE Wysyła dane wyjściowe za pomocą makra [TRACE.](#trace) Makro TRACE generuje dane wyjściowe tylko w kompilacjach debugowania; generuje żadnych danych wyjściowych w kompilacjach wydania. Ponadto TRACE mogą być przekierowywane do innych obiektów docelowych oprócz debugera.

- AFX_STACK_DUMP_TARGET_DEFAULT Wysyła dane wyjściowe zrzutu do domyślnego obiektu docelowego. W przypadku kompilacji debugowania dane wyjściowe przechodzą do makra TRACE. W kompilacji wydania dane wyjściowe przechodzi do Schowka.

- AFX_STACK_DUMP_TARGET_CLIPBOARD Wysyła dane wyjściowe tylko do Schowka. Dane są umieszczane w Schowku jako zwykły tekst w formacie CF_TEXT Schowek.

- AFX_STACK_DUMP_TARGET_BOTH Jednocześnie wysyła dane wyjściowe do Schowka i do makra TRACE.

- AFX_STACK_DUMP_TARGET_ODS Wysyła dane wyjściowe bezpośrednio do debugera za `OutputDebugString()`pomocą funkcji Win32 . Ta opcja wygeneruje dane wyjściowe debugera w kompilacjach debugowania i wydania, gdy debuger jest dołączony do procesu. AFX_STACK_DUMP_TARGET_ODS zawsze dociera do debugera (jeśli jest dołączony) i nie można go przekierować.

### <a name="remarks"></a>Uwagi

Poniższy przykład odzwierciedla pojedynczy wiersz danych wyjściowych generowanych na podstawie wywołania `AfxDumpStack` z obsługi przycisków w aplikacji okna dialogowego MFC:

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

Każdy wiersz w danych wyjściowych powyżej wskazuje adres ostatniego wywołania funkcji, pełną nazwę ścieżki modułu, który zawiera wywołanie funkcji i prototyp funkcji o nazwie. Jeśli wywołanie funkcji na stosie nie odbywa się pod dokładnym adresem funkcji, wyświetlane jest przesunięcie bajtów.

Na przykład w poniższej tabeli opisano pierwszy wiersz powyższego wyjścia:

|Dane wyjściowe|Opis|
|------------|-----------------|
|`00427D55:`|Adres zwrotny ostatniego wywołania funkcji.|
|`DUMP2\DEBUG\DUMP2.EXE!`|Pełna nazwa ścieżki modułu zawierającego wywołanie funkcji.|
|`void AfxDumpStack(unsigned long)`|Prototyp funkcji o nazwie.|
|`+ 181 bytes`|Przesunięcie w bajtach z adresu prototypu funkcji (w tym `void AfxDumpStack(unsigned long)`przypadku) do adresu `00427D55`zwrotnego (w tym przypadku).|

`AfxDumpStack`jest dostępny w wersjach debugowania i nondebug bibliotek MFC; jednak funkcja jest zawsze połączone statycznie, nawet wtedy, gdy plik wykonywalny używa MFC w udostępnionej biblioteki DLL. W implementacjach biblioteki udostępnionej funkcja znajduje się w MFCS42. Biblioteka LIB (i jej warianty).

Aby pomyślnie korzystać z tej funkcji:

- Plik IMAGEHLP. DLL musi znajdować się na ścieżce. Jeśli nie masz tej biblioteki DLL, funkcja wyświetli komunikat o błędzie. Zobacz [Biblioteka pomocy obrazów, aby](/windows/win32/Debug/image-help-library) uzyskać informacje na temat zestawu funkcji dostarczonych przez IMAGEHLP.

- Moduły, które mają ramki na stosie musi zawierać informacje debugowania. Jeśli nie zawierają informacji debugowania, funkcja będzie nadal generować ślad stosu, ale śledzenia będzie mniej szczegółowe.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump

Włącza i wyłącza zrzut przecieku pamięci w AFX_DEBUG_STATE destruktora.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Parametry

*bDump (właś)*<br/>
[w] Funkcja TRUE wskazuje, że zrzut przecieku pamięci jest włączony; FALSE wskazuje, że zrzut przecieku pamięci jest wyłączony.

### <a name="return-value"></a>Wartość zwracana

Poprzednia wartość dla tej flagi.

### <a name="remarks"></a>Uwagi

Gdy aplikacja zwalnia biblioteki MFC, biblioteka MFC sprawdza przecieki pamięci. W tym momencie wszelkie przecieki pamięci są zgłaszane do użytkownika za pośrednictwem okna **debugowania** programu Visual Studio.

Jeśli aplikacja ładuje inną bibliotekę przed biblioteką MFC, niektóre alokacje pamięci w tej bibliotece zostaną niepoprawnie zgłoszone jako przecieki pamięci. Przecieki pamięci false może spowodować, że aplikacja do zamknięcia powoli, jak biblioteka MFC zgłasza je. W takim przypadku `AfxEnableMemoryLeakDump` należy użyć, aby wyłączyć zrzut przeciek pamięci.

> [!NOTE]
> Jeśli ta metoda jest używana do wyłączania zrzutu przecieku pamięci, nie otrzymasz raportów o prawidłowych przecieków pamięci w aplikacji. Tej metody należy używać tylko wtedy, gdy masz pewność, że raport przecieku pamięci zawiera fałszywe przecieki pamięci.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxenablememorytracking"></a><a name="afxenablememorytracking"></a>AfxEnableMemoryTracking (Śledzenie)

Śledzenie pamięci diagnostycznej jest zwykle włączone w wersji debugowania MFC.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Parametry

*bTrack (śledzenie)*<br/>
Ustawienie tej wartości na TRUE włącza śledzenie pamięci; FALSE wyłącza go.

### <a name="return-value"></a>Wartość zwracana

Poprzednie ustawienie flagi tracking-enable.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do wyłączania śledzenia w sekcjach kodu, które wiesz, że przydzielają bloki poprawnie.

Aby uzyskać `AfxEnableMemoryTracking`więcej informacji na temat , zobacz [Debugowanie aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Ta funkcja działa tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIsMemoryBlock

Testuje adres pamięci, aby upewnić się, że reprezentuje aktualnie aktywny blok pamięci, który został przydzielony przez diagnostyczną wersję **nowego**.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskazuje blok pamięci do przetestowania.

*n Bajty*<br/>
Zawiera długość bloku pamięci w bajtach.

*numer plRequestNumber*<br/>
Wskazuje **długą** liczbę całkowitą, która zostanie wypełniona numerem sekwencyjnym alokacji bloku pamięci lub zerem, jeśli nie reprezentuje aktualnie aktywnego bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli blok pamięci jest obecnie przydzielony, a długość jest poprawna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Sprawdza również określony rozmiar względem oryginalnego rozmiaru przydzielonego. Jeśli funkcja zwraca wartość niezerową, numer sekwencyjny alokacji jest zwracany w *plRequestNumber*. Ta liczba reprezentuje kolejność, w jakiej blok został przydzielony względem wszystkich innych **nowych** alokacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValidAddress

Testuje dowolny adres pamięci, aby upewnić się, że jest on zawarty w całości w przestrzeni pamięci programu.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Parametry

*Lp*<br/>
Wskazuje adres pamięci, który ma zostać przetestowany.

*n Bajty*<br/>
Zawiera liczbę bajtów pamięci do przetestowania.

*bPrzepisy*<br/>
Określa, czy pamięć jest zarówno do odczytu i zapisu (PRAWDA), czy tylko do odczytu (FALSE).

### <a name="return-value"></a>Wartość zwracana

W kompilacjach debugowania, niezerowe, jeśli określony blok pamięci jest zawarty w całości w przestrzeni pamięci programu; w przeciwnym razie 0.

W kompilacjach innych niż debugowanie, niezerowe, jeśli *lp* nie jest NULL; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Adres nie jest ograniczony do bloków przydzielonych przez **nowe**.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIsValidString (AfxIsValidString)

Ta funkcja służy do określenia, czy wskaźnik do ciągu jest prawidłowy.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>Parametry

*lpsz (lpsz)*<br/>
Wskaźnik do przetestowania.

*nLength (nLength)*<br/>
Określa długość ciągu, który ma być testowany w bajtach. Wartość -1 wskazuje, że ciąg zostanie zakończony zerem.

### <a name="return-value"></a>Wartość zwracana

W kompilacjach debugowania, niezerowe, jeśli określony wskaźnik wskazuje na ciąg o określonym rozmiarze; w przeciwnym razie 0.

W kompilacjach innych niż debugowanie, niezerowe, jeśli *lpsz* nie ma wartości NULL; w przeciwnym razie 0.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxsetallochook"></a><a name="afxsetallochook"></a>AfxSetAllocHook (AfxSetAllocHook)

Ustawia hak, który umożliwia wywołanie określonej funkcji przed przydzieleniem każdego bloku pamięci.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Parametry

*pfnAllocHook*<br/>
Określa nazwę funkcji do wywołania. Zobacz Uwagi dla prototypu funkcji alokacji.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli chcesz zezwolić na alokację; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Alokator pamięci debugowania biblioteki klasy firmy Microsoft Foundation może wywołać zdefiniowaną przez użytkownika funkcję haka, aby umożliwić użytkownikowi monitorowanie alokacji pamięci i kontrolowanie, czy alokacja jest dozwolona. Funkcje haka alokacji są prototypowane w następujący sposób:

**BOOL AFXAPI AllocHook( size_t** `nSize` **, BOOL** `bObject` **, LONG** `lRequestNumber` **);**

*nSize (rozmiar)*<br/>
Rozmiar proponowanej alokacji pamięci.

*bObiekt*<br/>
PRAWDA, jeśli alokacja `CObject`jest dla obiektu pochodnego; w przeciwnym razie FALSE.

*lRequestNumber*<br/>
Numer sekwencyjny alokacji pamięci.

Należy zauważyć, że konwencja wywoływania AFXAPI oznacza, że wywoływany musi usunąć parametry ze stosu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxdoforallclasses"></a><a name="afxdoforallclasses"></a>AfxDoForAllClasses (Klasy AfxDoForAll)

Wywołuje określoną funkcję iteracji dla `CObject`wszystkich klasy pochodne serializable w przestrzeni pamięci aplikacji.

```cpp
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*Pfn*<br/>
Wskazuje funkcję iteracji, która ma być wywoływana dla każdej klasy. Argumenty funkcji są wskaźnikiem `CRuntimeClass` do obiektu i wskaźnik void do dodatkowych danych, które obiekt wywołujący dostarcza do funkcji.

*Pcontext*<br/>
Wskazuje na dane opcjonalne, które wywołujący może podać do funkcji iteracji. Ten wskaźnik może mieć wartość NULL.

### <a name="remarks"></a>Uwagi

Klasy pochodne serializowalne `CObject`są klasami pochodnymi przy użyciu makra DECLARE_SERIAL. Wskaźnik, który jest `AfxDoForAllClasses` przekazywany do w *pContext* jest przekazywana do określonej funkcji iteracji za każdym razem, gdy jest wywoływana.

> [!NOTE]
> Ta funkcja działa tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDoForAllObjects afxdoforallobjects AfxDoForAllObjects Afx

Wykonuje określoną funkcję iteracji dla wszystkich `CObject` obiektów pochodzących z tych, które zostały przydzielone z **nowym**.

```cpp
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parametry

*Pfn*<br/>
Wskazuje funkcję iteracji do wykonania dla każdego obiektu. Argumenty funkcji są wskaźnikiem `CObject` do i wskaźnik void do dodatkowych danych, które wywołujący dostarcza do funkcji.

*Pcontext*<br/>
Wskazuje na dane opcjonalne, które wywołujący może podać do funkcji iteracji. Ten wskaźnik może mieć wartość NULL.

### <a name="remarks"></a>Uwagi

Obiekty stosu, globalne lub osadzone nie są wyliczane. Wskaźnik przekazany `AfxDoForAllObjects` do w *pContext* jest przekazywana do określonej funkcji iteracji za każdym razem, gdy jest wywoływana.

> [!NOTE]
> Ta funkcja działa tylko w wersji debugowania MFC.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)<br/>
[CObject::Dump](cobject-class.md#dump)
