---
title: Makra i funkcje do zarządzania bibliotekami DLL
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: 42a08ff2e806acae6713c9df3fe170f7e89f05af
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751601"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makra i funkcje do zarządzania bibliotekami DLL

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Eksportuje klasy.|
|[Afx_manage_state](#afx_manage_state)|Chroń wyeksportowane funkcje w biblioteki DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Zapewnia obsługę OLE z zwykłej biblioteki DLL MFC, która jest dynamicznie połączona z MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Zapewnia obsługę gniazd MFC z regularnej biblioteki DLL MFC, która jest dynamicznie połączona z MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Pobiera bieżący stan flagi stanu na moduł.|
|[AfxGetStaticModuleState AfxGetStaticModuleState AfxGetStaticModuleState Afx](#afxgetstaticmodulestate)|Ustawia stan modułu przed inicjacją i/lub przywrócić poprzedni stan modułu po oczyszczeniu.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Inicjuje bibliotekę DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|ustaw flagę stanu na moduł, co wpływa na zachowanie Usługi WinSxS MFC.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Umożliwia MFC oczyścić DLL rozszerzenia MFC, gdy każdy proces odłącza się od biblioteki DLL.|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a>Afx_ext_class

[Biblioteki DLL rozszerzenia MFC](../../build/extension-dlls.md) używają AFX_EXT_CLASS makr do eksportowania klas; pliki wykonywalne, które łączą się z biblioteką DLL rozszerzenia MFC, używają makra do importowania klas.

### <a name="remarks"></a>Uwagi

W przypadku makra AFX_EXT_CLASS ten sam plik nagłówka używany do tworzenia biblioteki DLL rozszerzenia MFC może być używany z plikami wykonywalnymi łączącymi się z biblioteką DLL.

W pliku nagłówka biblioteki DLL dodaj słowo kluczowe AFX_EXT_CLASS do deklaracji klasy w następujący sposób:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Aby uzyskać więcej informacji, zobacz [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxv_dll.h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a>Afx_manage_state

Wywołanie tego makra w celu ochrony wyeksportowanej funkcji w dll.

### <a name="syntax"></a>Składnia

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parametry

*pPoseł Stan*<br/>
Wskaźnik do `AFX_MODULE_STATE` struktury.

### <a name="remarks"></a>Uwagi

Gdy to makro jest wywoływane, *pModuleState* jest stan modułu skuteczne dla pozostałej części bezpośredniego zawierające zakres. Po opuszczeniu zakresu poprzedni stan modułu efektywnego zostanie automatycznie przywrócony.
Struktura `AFX_MODULE_STATE` zawiera dane globalne dla modułu, czyli część stanu modułu, który jest wypychany lub wyskoczył.

Domyślnie MFC używa dojścia zasobów aplikacji głównej do załadowania szablonu zasobu. Jeśli masz wyeksportowaną funkcję w dll, takich jak ten, który uruchamia okno dialogowe w dll, ten szablon jest rzeczywiście przechowywane w module DLL. Należy przełączyć stan modułu, aby używany był odpowiedni uchwyt. Można to zrobić, dodając następujący kod na początku funkcji:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Spowoduje to zamianę bieżącego stanu modułu ze stanem zwróconym z [AfxGetStaticModuleState](#afxgetstaticmodulestate) do końca bieżącego zakresu.

Aby uzyskać więcej informacji na temat stanów modułów i MFC, zobacz "Zarządzanie danymi o stanie modułów MFC" w [temacie Tworzenie nowych dokumentów, systemu Windows i widoków](../creating-new-documents-windows-and-views.md) oraz [uwagi technicznej 58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
> Gdy MFC tworzy kontekst aktywacji dla zestawu, używa [AfxWinInit](application-information-and-management.md#afxwininit) do tworzenia kontekstu i `AFX_MANAGE_STATE` aktywować i dezaktywować go. Należy również `AFX_MANAGE_STATE` zauważyć, że jest włączona dla statycznych bibliotek MFC, a także bibliotek DLL MFC, aby umożliwić kod MFC do wykonania w kontekście aktywacji wybranego przez bibliotekę DLL użytkownika. Aby uzyskać więcej informacji, zobacz [Obsługa kontekstów aktywacji w stanie modułu MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxstat_.h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/>AfxOleInitModule

W przypadku obsługi OLE z zwykłej biblioteki DLL MFC, która jest dynamicznie połączona z MFC, wywołanie tej funkcji w funkcji zwykłej `CWinApp::InitInstance` biblioteki DLL MFC, aby zainicjować bibliotekę DLL OLE MFC.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Uwagi

Biblioteka DLL OLE MFC jest biblioteką DLL rozszerzenia MFC; aby biblioteka DLL rozszerzenia MFC została `CDynLinkLibrary` podłączona do łańcucha, musi utworzyć `CDynLinkLibrary` obiekt w kontekście każdego modułu, który będzie go używał. `AfxOleInitModule`tworzy `CDynLinkLibrary` obiekt w kontekście regularnych bibliotek DLL MFC, tak `CDynLinkLibrary` aby pobierał podłączony do łańcucha obiektów zwykłej biblioteki DLL MFC.

Jeśli budujesz formant OLE `COleControlModule`i używasz `AfxOleInitModule` , `InitInstance` nie należy `COleControlModule` `AfxOleInitModule`wywoływać, ponieważ funkcja elementu członkowskiego dla wywołań .

### <a name="requirements"></a>Wymagania

**Nagłówek** \<: afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a>AfxNetInitModule

W przypadku obsługi gniazd MFC z zwykłej biblioteki DLL MFC, która jest dynamicznie połączona z `CWinApp::InitInstance` MFC, dodaj wywołanie tej funkcji w funkcji zwykłej biblioteki DLL MFC, aby zainicjować bibliotekę DLL MFC Sockets.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Uwagi

Biblioteka DLL MFC Sockets jest biblioteką DLL rozszerzenia MFC; aby biblioteka DLL rozszerzenia MFC została `CDynLinkLibrary` podłączona do łańcucha, musi utworzyć `CDynLinkLibrary` obiekt w kontekście każdego modułu, który będzie go używał. `AfxNetInitModule`tworzy `CDynLinkLibrary` obiekt w kontekście regularnych bibliotek DLL MFC, tak `CDynLinkLibrary` aby pobierał podłączony do łańcucha obiektów zwykłej biblioteki DLL MFC.

### <a name="requirements"></a>Wymagania

**Nagłówek:** \<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a>AfxGetAmbientActCtx

Ta funkcja służy do uzyskania bieżącego stanu flagi stanu na moduł, co wpływa na zachowanie WinSxS MFC.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość flagi stanu modułu.

### <a name="remarks"></a>Uwagi

Gdy flaga jest ustawiona (co jest domyślna) i wątek wchodzi do modułu MFC (patrz [AFX_MANAGE_STATE),](#afx_manage_state)kontekst modułu jest aktywowany.

Jeśli flaga nie jest ustawiona, kontekst modułu nie jest aktywowany przy wprowadzaniu.

Kontekst modułu jest określany na podstawie jego manifestu, zwykle osadzonego w zasobach modułu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a>AfxGetStaticModuleState AfxGetStaticModuleState AfxGetStaticModuleState Afx

Wywołanie tej funkcji, aby ustawić stan modułu przed inicjacją i/lub przywrócić poprzedni stan modułu po oczyszczeniu.

### <a name="syntax"></a>Składnia

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `AFX_MODULE_STATE` struktury.

### <a name="remarks"></a>Uwagi

Struktura `AFX_MODULE_STATE` zawiera dane globalne dla modułu, czyli część stanu modułu, który jest wypychany lub wyskoczył.

Domyślnie MFC używa dojścia zasobów aplikacji głównej do załadowania szablonu zasobu. Jeśli masz wyeksportowaną funkcję w dll, takich jak ten, który uruchamia okno dialogowe w dll, ten szablon jest rzeczywiście przechowywane w module DLL. Należy przełączyć stan modułu, aby używany był odpowiedni uchwyt. Można to zrobić, dodając następujący kod na początku funkcji:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Spowoduje to zamianę bieżącego stanu `AfxGetStaticModuleState` modułu ze stanem zwróconym od końca bieżącego zakresu.

Aby uzyskać więcej informacji na temat stanów modułów i MFC, zobacz "Zarządzanie danymi o stanie modułów MFC" w [temacie Tworzenie nowych dokumentów, systemu Windows i widoków](../creating-new-documents-windows-and-views.md) oraz [uwagi technicznej 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxstat_.h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Wywołanie tej funkcji w DLL `DllMain` rozszerzenia MFC, aby zainicjować bibliotekę DLL.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parametry

*Państwa*<br/>
Odwołanie do [AFX_EXTENSION_MODULE Structure](afx-extension-module-structure.md) struktury struktury, która będzie zawierać stan modułu DLL rozszerzenia MFC po inicjalizacji. Stan zawiera kopię obiektów klasy runtime, które zostały zainicjowane przez DLL rozszerzenia MFC jako `DllMain` część normalnej konstrukcji obiektu statycznego wykonane przed wprowadzeniem.

*hModule*<br/>
Dojście modułu DLL rozszerzenia MFC.

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli biblioteka DLL rozszerzenia MFC została pomyślnie zainicjowana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Przykład:

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;
...
```

`AfxInitExtensionModule`tworzy kopię biblioteki DLL HMODULE i przechwytuje dll's runtime-klasy (struktury),`CRuntimeClass` jak również`COleObjectFactory` jego fabryk obiektów (obiekty) do użycia później podczas tworzenia `CDynLinkLibrary` obiektu.
Biblioteki DLL rozszerzenia MFC muszą `DllMain` wykonać dwie czynności w swojej funkcji:

- Wywołanie [AfxInitExtensionModule](#afxinitextensionmodule) i sprawdź wartość zwracaną.

- Utwórz `CDynLinkLibrary` obiekt, jeśli biblioteka DLL będzie eksportować obiekty [CRuntimeClass Structure](cruntimeclass-structure.md) lub ma własne zasoby niestandardowe.

Można wywołać, `AfxTermExtensionModule` aby wyczyścić bibliotekę DLL rozszerzenia MFC, gdy każdy proces odłącza się od biblioteki DLL rozszerzenia MFC `AfxFreeLibrary` (co się dzieje, gdy proces kończy działanie lub gdy biblioteka DLL jest zwalniana w wyniku wywołania).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdll_.h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a>AfxSetAmbientActCtx

Ta funkcja służy do ustawiania flagi stanu dla modułu, co wpływa na zachowanie WinSxS MFC.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parametry

*bStaw*<br/>
Nowa wartość flagi stanu modułu.

### <a name="remarks"></a>Uwagi

Gdy flaga jest ustawiona (co jest domyślna) i wątek wchodzi do modułu MFC (patrz [AFX_MANAGE_STATE),](#afx_manage_state)kontekst modułu jest aktywowany.
Jeśli flaga nie jest ustawiona, kontekst modułu nie jest aktywowany przy wprowadzaniu.
Kontekst modułu jest określany na podstawie jego manifestu, zwykle osadzonego w zasobach modułu.

### <a name="example"></a>Przykład

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxcomctl32.h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a>AfxTermExtensionModule

Wywołanie tej funkcji, aby umożliwić MFC oczyścić bibliotekę DLL rozszerzenia MFC, gdy każdy proces odłącza się od biblioteki DLL `AfxFreeLibrary` (co dzieje się po zakończeniu procesu lub gdy biblioteka DLL jest zwalniana w wyniku wywołania).

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parametry

*Państwa*<br/>
Odwołanie do [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) struktury, która zawiera stan modułu DLL rozszerzenia MFC.

*Piłkę*<br/>
Jeśli true, oczyścić wszystkie moduły DLL rozszerzenia MFC. W przeciwnym razie należy wyczyścić tylko bieżący moduł biblioteki DLL.

### <a name="remarks"></a>Uwagi

`AfxTermExtensionModule`usunie wszystkie lokalne magazyny dołączone do modułu i usunie wszystkie wpisy z pamięci podręcznej mapy wiadomości. Przykład:

```cpp
static AFX_EXTENSION_MODULE NVC_MFC_DLLDLL = { NULL, NULL };
extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
    // Remove this if you use lpReserved
    UNREFERENCED_PARAMETER(lpReserved);

    if (dwReason == DLL_PROCESS_ATTACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Initializing!\n");

        // MFC extension DLL one-time initialization
        if (!AfxInitExtensionModule(NVC_MFC_DLLDLL, hInstance))
            return 0;

        new CMyDynLinkLibrary(NVC_MFC_DLLDLL);

    }
    else if (dwReason == DLL_PROCESS_DETACH)
    {
        TRACE0("NVC_MFC_DLL.DLL Terminating!\n");

        // Terminate the library before destructors are called
        AfxTermExtensionModule(NVC_MFC_DLLDLL);
    }
    return 1;   // ok
}
```

Jeśli aplikacja dynamicznie ładuje i zwalnia biblioteki DLL rozszerzenia `AfxTermExtensionModule`MFC, należy wywołać . Ponieważ większość bibliotek DLL rozszerzenia MFC nie są ładowane dynamicznie (zwykle `AfxTermExtensionModule` są one połączone za pośrednictwem bibliotek importu), wywołanie zwykle nie jest konieczne.

Rozszerzenie MFC biblioteki DLL muszą wywołać [AfxInitExtensionModule](#afxinitextensionmodule) w ich `DllMain`. Jeśli biblioteka DLL będzie eksportować obiekty [CRuntimeClass](cruntimeclass-structure.md) lub ma własne `CDynLinkLibrary` zasoby `DllMain`niestandardowe, należy również utworzyć obiekt w pliku .

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdll_.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)<br/>
[Afxmessagebox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Zarządzanie danymi stanu modułów MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
