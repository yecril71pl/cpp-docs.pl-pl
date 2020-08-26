---
title: Makra i funkcje do zarządzania bibliotekami DLL
ms.date: 03/27/2019
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: e4170ba95775fd3380837673a76a8adafc8ad011
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837184"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makra i funkcje do zarządzania bibliotekami DLL

|Nazwa|Opis|
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Eksportuje klasy.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Ochrona wyeksportowanej funkcji w bibliotece DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Zapewnia obsługę OLE przy użyciu zwykłej biblioteki MFC DLL, która jest dynamicznie połączona z MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Zapewnia obsługę funkcji MFC Sockets ze zwykłej biblioteki MFC DLL, która jest dynamicznie połączona z MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Pobiera bieżący stan flagi stanu dla modułu.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Ustawia stan modułu przed inicjalizacją i/lub przywraca poprzedni stan modułu po oczyszczeniu.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Inicjuje bibliotekę DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|Ustaw flagę stanu dla modułu, która ma wpływ na zachowanie WinSxS MFC.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Umożliwia MFC czyszczenie biblioteki DLL rozszerzenia MFC, gdy każdy proces odłącza się od biblioteki DLL.|

## <a name="afx_ext_class"></a><a name="afx_ext_class"></a> AFX_EXT_CLASS

[Biblioteki DLL rozszerzenia MFC](../../build/extension-dlls.md) używają AFX_EXT_CLASS makro do eksportowania klas; Pliki wykonywalne łączące się z biblioteką DLL rozszerzenia MFC używają makra do importowania klas.

### <a name="remarks"></a>Uwagi

Za pomocą makra AFX_EXT_CLASS te same pliki nagłówkowe, które służą do kompilowania biblioteki DLL rozszerzenia MFC mogą być używane z plikami wykonywalnymi, które łączą się z biblioteką DLL.

W pliku nagłówkowym biblioteki DLL Dodaj słowo kluczowe AFX_EXT_CLASS do deklaracji klasy w następujący sposób:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Aby uzyskać więcej informacji, zobacz [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXV_DLL. h

## <a name="afx_manage_state"></a><a name="afx_manage_state"></a> AFX_MANAGE_STATE

Wywołaj to makro, aby chronić funkcję eksportowaną w bibliotece DLL.

### <a name="syntax"></a>Składnia

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parametry

*pModuleState*<br/>
Wskaźnik do `AFX_MODULE_STATE` struktury.

### <a name="remarks"></a>Uwagi

Po wywołaniu tego makra *pModuleState* jest efektywnym stanem modułu dla pozostałej części bezpośredniego zawierającego go zakresu. Po opuszczeniu zakresu poprzedni stan obowiązującego modułu zostanie automatycznie przywrócony.
`AFX_MODULE_STATE`Struktura zawiera dane globalne dla modułu, czyli część stanu modułu, który jest wypychany lub zdjęte.

Domyślnie MFC używa dojścia do zasobów głównej aplikacji do ładowania szablonu zasobu. W przypadku wyeksportowanej funkcji w bibliotece DLL, takiej jak ta, która powoduje uruchomienie okna dialogowego w bibliotece DLL, ten szablon jest faktycznie przechowywany w module DLL. Należy przełączyć stan modułu, aby można było użyć prawidłowego uchwytu. Można to zrobić, dodając następujący kod na początku funkcji:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Spowoduje to zamianę bieżącego stanu modułu na stan zwrócony z [AfxGetStaticModuleState](#afxgetstaticmodulestate) do końca bieżącego zakresu.

Aby uzyskać więcej informacji na temat stanów modułów i MFC, zobacz "Zarządzanie danymi stanu modułów MFC" w temacie [Tworzenie nowych dokumentów, okien i widoków](../creating-new-documents-windows-and-views.md) oraz [uwagi technicznej 58](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
> Gdy MFC tworzy kontekst aktywacji dla zestawu, używa [AfxWinInit](application-information-and-management.md#afxwininit) do tworzenia kontekstu i `AFX_MANAGE_STATE` aktywowania i dezaktywowania go. Należy również pamiętać, że `AFX_MANAGE_STATE` włączono obsługę statycznych BIBLIOTEK MFC, a także BIBLIOTEK MFC DLL, aby umożliwić wykonywanie kodu MFC w odpowiednim kontekście aktywacji wybranym przez użytkownika dll. Aby uzyskać więcej informacji, zobacz [Obsługa kontekstów aktywacji w stanie modułu MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxstat_. h

## <a name="a-nameafxoleinitmodule-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> AfxOleInitModule

Aby zapewnić obsługę OLE ze zwykłej biblioteki MFC DLL, która jest dynamicznie połączona z MFC, Wywołaj tę funkcję w funkcji regularnej biblioteki DLL MFC, `CWinApp::InitInstance` Aby zainicjować bibliotekę MFC OLE dll.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Uwagi

Biblioteka MFC OLE DLL jest biblioteką DLL rozszerzenia MFC; Aby biblioteka DLL rozszerzenia MFC mogła zostać podłączona do `CDynLinkLibrary` łańcucha, musi utworzyć `CDynLinkLibrary` obiekt w kontekście każdego modułu, który będzie go używać. `AfxOleInitModule` tworzy `CDynLinkLibrary` obiekt w kontekście regularnej biblioteki DLL MFC, dzięki czemu będzie on połączony z `CDynLinkLibrary` łańcuchem obiektów zwykłej biblioteki MFC DLL.

Jeśli tworzysz formant OLE i używasz `COleControlModule` , nie należy wywoływać, `AfxOleInitModule` ponieważ `InitInstance` funkcja członkowska dla `COleControlModule` wywołań `AfxOleInitModule` .

### <a name="requirements"></a>Wymagania

**Nagłówek**: \<afxdll_.h>

## <a name="afxnetinitmodule"></a><a name="afxnetinitmodule"></a> AfxNetInitModule

W przypadku obsługi usługi MFC Sockets ze zwykłej biblioteki MFC DLL, która jest dynamicznie połączona z MFC, Dodaj wywołanie tej funkcji w funkcji regularnej biblioteki DLL MFC, `CWinApp::InitInstance` Aby zainicjować bibliotekę DLL usługi MFC Sockets.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Uwagi

Biblioteka DLL Sockets MFC jest biblioteką DLL rozszerzenia MFC; Aby biblioteka DLL rozszerzenia MFC mogła zostać podłączona do `CDynLinkLibrary` łańcucha, musi utworzyć `CDynLinkLibrary` obiekt w kontekście każdego modułu, który będzie go używać. `AfxNetInitModule` tworzy `CDynLinkLibrary` obiekt w kontekście regularnej biblioteki DLL MFC, dzięki czemu będzie on połączony z `CDynLinkLibrary` łańcuchem obiektów zwykłej biblioteki MFC DLL.

### <a name="requirements"></a>Wymagania

**Nagłówek:**\<afxdll_.h>

## <a name="afxgetambientactctx"></a><a name="afxgetambientactctx"></a> AfxGetAmbientActCtx

Użyj tej funkcji, aby uzyskać bieżący stan flagi stanu dla modułu, która ma wpływ na zachowanie WinSxS MFC.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Wartość zwracana

Bieżąca wartość flagi stanu modułu.

### <a name="remarks"></a>Uwagi

Po ustawieniu flagi (co jest ustawieniem domyślnym), a wątek przechodzi do modułu MFC (zobacz [AFX_MANAGE_STATE](#afx_manage_state)), kontekst modułu jest aktywowany.

Jeśli flaga nie jest ustawiona, kontekst modułu nie jest aktywowany przy wpisie.

Kontekst modułu jest określany na podstawie jego manifestu, zazwyczaj osadzony w zasobach modułu.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxcomctl32. h

## <a name="afxgetstaticmodulestate"></a><a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState

Wywołaj tę funkcję, aby ustawić stan modułu przed inicjalizacją i/lub przywrócić poprzedni stan modułu po oczyszczeniu.

### <a name="syntax"></a>Składnia

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `AFX_MODULE_STATE` struktury.

### <a name="remarks"></a>Uwagi

`AFX_MODULE_STATE`Struktura zawiera dane globalne dla modułu, czyli część stanu modułu, który jest wypychany lub zdjęte.

Domyślnie MFC używa dojścia do zasobów głównej aplikacji do ładowania szablonu zasobu. W przypadku wyeksportowanej funkcji w bibliotece DLL, takiej jak ta, która powoduje uruchomienie okna dialogowego w bibliotece DLL, ten szablon jest faktycznie przechowywany w module DLL. Należy przełączyć stan modułu, aby można było użyć prawidłowego uchwytu. Można to zrobić, dodając następujący kod na początku funkcji:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Spowoduje to zamianę bieżącego stanu modułu na stan zwrócony z `AfxGetStaticModuleState` do momentu zakończenia bieżącego zakresu.

Aby uzyskać więcej informacji na temat stanów modułów i MFC, zobacz "Zarządzanie danymi stanu modułów MFC" w temacie [Tworzenie nowych dokumentów, okien i widoków](../creating-new-documents-windows-and-views.md) oraz [uwagi technicznej 58](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxstat_. h

## <a name="afxinitextensionmodule"></a>AfxInitExtensionModule

Wywołaj tę funkcję w bibliotece DLL rozszerzenia MFC, `DllMain` Aby zainicjować bibliotekę DLL.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parametry

*Państwu*<br/>
Odwołanie do struktury [struktury AFX_EXTENSION_MODULE](afx-extension-module-structure.md) , która będzie zawierać stan modułu DLL rozszerzenia MFC po zainicjowaniu. Stan zawiera kopię obiektów klasy środowiska uruchomieniowego, które zostały zainicjowane przez bibliotekę DLL rozszerzenia MFC jako część normalnej konstrukcji obiektu statycznego wykonane przed `DllMain` wprowadzeniem.

*hModule*<br/>
Dojście modułu DLL rozszerzenia MFC.

### <a name="return-value"></a>Wartość zwracana

Ma wartość TRUE, jeśli biblioteka DLL rozszerzenia MFC została pomyślnie zainicjowana; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Na przykład:

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

`AfxInitExtensionModule` tworzy kopię HMODULE biblioteki DLL i przechwytuje klasy środowiska uruchomieniowego bibliotek DLL ( `CRuntimeClass` struktury) oraz ich fabryki obiektów `COleObjectFactory` do użycia w przyszłości podczas `CDynLinkLibrary` tworzenia obiektu.
Biblioteki DLL rozszerzenia MFC muszą wykonywać dwie rzeczy w `DllMain` funkcji:

- Wywołaj [AfxInitExtensionModule](#afxinitextensionmodule) i sprawdź wartość zwracaną.

- Utwórz `CDynLinkLibrary` obiekt, jeśli biblioteka DLL będzie eksportować obiekty [struktury CRuntimeClass](cruntimeclass-structure.md) lub ma własne zasoby niestandardowe.

Można wywołać `AfxTermExtensionModule` , aby wyczyścić bibliotekę DLL rozszerzenia MFC, gdy każdy proces zostanie odłączony od biblioteki DLL rozszerzenia MFC (co się stanie w momencie zakończenia procesu lub gdy biblioteka DLL zostanie zwolniona w wyniku `AfxFreeLibrary` wywołania).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDLL_. h

## <a name="afxsetambientactctx"></a><a name="afxsetambientactctx"></a> AfxSetAmbientActCtx

Ta funkcja służy do ustawiania flagi stanu dla modułu, która ma wpływ na zachowanie WinSxS MFC.

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parametry

*bSet*<br/>
Nowa wartość flagi stanu modułu.

### <a name="remarks"></a>Uwagi

Po ustawieniu flagi (co jest ustawieniem domyślnym), a wątek przechodzi do modułu MFC (zobacz [AFX_MANAGE_STATE](#afx_manage_state)), kontekst modułu jest aktywowany.
Jeśli flaga nie jest ustawiona, kontekst modułu nie jest aktywowany przy wpisie.
Kontekst modułu jest określany na podstawie jego manifestu, zazwyczaj osadzony w zasobach modułu.

### <a name="example"></a>Przykład

```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
}
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxcomctl32. h

## <a name="afxtermextensionmodule"></a><a name="afxtermextensionmodule"></a> AfxTermExtensionModule

Wywołaj tę funkcję, aby umożliwić MFC czyszczenie biblioteki DLL rozszerzenia MFC, gdy każdy proces odłącza się od biblioteki DLL (co się stanie po zakończeniu procesu lub gdy biblioteka DLL zostanie zwolniona w wyniku `AfxFreeLibrary` wywołania).

### <a name="syntax"></a>Składnia

```cpp
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parametry

*Państwu*<br/>
Odwołanie do struktury [AFX_EXTENSION_MODULE](afx-extension-module-structure.md) , która zawiera stan modułu DLL rozszerzenia MFC.

*Klika*<br/>
W przypadku wartości TRUE Wyczyść wszystkie moduły DLL rozszerzenia MFC. W przeciwnym razie wyczyść tylko bieżący moduł DLL.

### <a name="remarks"></a>Uwagi

`AfxTermExtensionModule` spowoduje usunięcie wszystkich magazynów lokalnych podłączonych do modułu i usunięcie wszelkich wpisów z pamięci podręcznej mapy komunikatów. Na przykład:

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

Jeśli aplikacja ładuje i zwalnia biblioteki DLL rozszerzenia MFC dynamicznie, należy wywołać metodę `AfxTermExtensionModule` . Ponieważ większość bibliotek DLL rozszerzeń MFC nie są ładowane dynamicznie (zazwyczaj są one połączone za pośrednictwem ich bibliotek importu), wywołanie `AfxTermExtensionModule` jest zwykle niepotrzebne.

Biblioteki DLL rozszerzeń MFC muszą wywoływać [AfxInitExtensionModule](#afxinitextensionmodule) `DllMain` . Jeśli biblioteka DLL będzie eksportować obiekty [CRuntimeClass](cruntimeclass-structure.md) lub ma własne zasoby niestandardowe, należy również utworzyć `CDynLinkLibrary` obiekt w `DllMain` .

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDLL_. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Zarządzanie danymi stanu modułów MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
