---
title: Makra i funkcje zarządzania biblioteki dll
ms.date: 04/03/2017
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
ms.openlocfilehash: 863350067c39fbc9cdb3d9d3a6c4448348d977de
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328769"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makra i funkcje zarządzania biblioteki dll

|||
|-|-|
|[AFX_EXT_CLASS](#afx_ext_class)]|Eksportowanie klas.|
|[AFX_MANAGE_STATE](#afx_manage_state)|Chroń eksportowanych funkcji w bibliotece DLL.|
|[AfxOleInitModule](#afxoleinitmodule)|Zapewnia obsługę OLE od zwykłej biblioteki MFC DLL, która jest połączona dynamicznie z MFC.|
|[AfxNetInitModule](#afxnetinitmodule)|Umożliwia obsługę MFC gniazd od zwykłej biblioteki MFC DLL, która jest połączona dynamicznie z MFC.|
|[AfxGetAmbientActCtx](#afxgetambientactctx)|Pobiera bieżący stan flagi stanu dla modułu.|
|[AfxGetStaticModuleState](#afxgetstaticmodulestate)|Ustawia stan modułu przed zainicjowaniem i/lub w celu przywrócenia poprzedniego stanu modułu po oczyszczaniu.|
|[AfxInitExtensionModule](#afxinitextensionmodule)|Inicjuje biblioteki DLL.|
|[AfxSetAmbientActCtx](#afxsetambientactctx)|Ustaw flagi stanu-module, który ma wpływ na zachowanie folderze WinSxS MFC.|
|[AfxTermExtensionModule](#afxtermextensionmodule)|Umożliwia MFC do oczyszczania biblioteki DLL rozszerzenia MFC podczas każdego procesu odłączy się od biblioteki DLL.|

## <a name="afx_ext_class"></a>  AFX_EXT_CLASS

[Biblioteki DLL rozszerzeń MFC](../../build/extension-dlls.md) użyj makra AFX_EXT_CLASS, aby wyeksportować klasy; pliki wykonywalne, które łączą się rozszerzenia MFC biblioteki DLL użyć makra, aby zaimportować klasy.

### <a name="remarks"></a>Uwagi

Przy użyciu makra AFX_EXT_CLASS tych samych plików nagłówka używany do tworzenia biblioteki DLL rozszerzenia MFC można łączyć z plików wykonywalnych, które łącze do biblioteki DLL.

W pliku nagłówka dla biblioteki DLL należy dodać AFX_EXT_CLASS — słowo kluczowe do deklaracji klasy w następujący sposób:

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

Aby uzyskać więcej informacji, zobacz [eksportu i importu za pomocą AFX_EXT_CLASS](../../build/exporting-and-importing-using-afx-ext-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxv_dll.h

## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE

Wywołanie tego makra, aby chronić eksportowanych funkcji w bibliotece DLL.

### <a name="syntax"></a>Składnia

```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )
```

### <a name="parameters"></a>Parametry

*pModuleState*<br/>
Wskaźnik do `AFX_MODULE_STATE` struktury.

### <a name="remarks"></a>Uwagi

Po wywołaniu tego makra *pModuleState* to skuteczne modułu stanu dla pozostałych bezpośrednio zawierający zakres. Po opuszczeniu zakres, poprzedniego stanu modułu skuteczne zostanie automatycznie przywrócona.
`AFX_MODULE_STATE` Struktura zawiera dane globalne dla modułu, oznacza to, że część stanu modułu, który jest przypisany lub zdjęte ze stosu.

Domyślnie MFC wykorzystuje uchwyt zasobów aplikacji głównej można załadować szablonu zasobów. Jeśli masz eksportowanych funkcji w bibliotece DLL, taki, który uruchamia okno dialogowe w bibliotece DLL, ten szablon rzeczywiście jest przechowywana w moduł biblioteki DLL. Musisz przełączyć stanu modułu na prawidłowy uchwyt do użycia. Można to zrobić, dodając następujący kod na początku funkcji:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Zamienia to bieżący stan modułu ze stanem zwróciło [AfxGetStaticModuleState —](#afxgetstaticmodulestate) aż do końca bieżącego zakresu.

Aby uzyskać więcej informacji na temat Stany modułu i MFC, zobacz temat "Zarządzanie stanu danych z MFC — moduły" w [tworzenie nowych dokumentów, Windows i widoki](../creating-new-documents-windows-and-views.md) i [techniczne 58 Uwaga](../tn058-mfc-module-state-implementation.md).

> [!NOTE]
>  Gdy MFC tworzy kontekst aktywacji dla zestawu, używa [afxwininit —](#afxwininit) można utworzyć kontekstu i `AFX_MANAGE_STATE` Włączanie i wyłączanie go. Należy zauważyć, że `AFX_MANAGE_STATE` jest włączona dla statycznej biblioteki MFC, a także biblioteki MFC dll, aby umożliwić kodu MFC można wykonać w kontekście właściwej aktywacji wybranych przez użytkownika pliku DLL. Aby uzyskać więcej informacji, zobacz [Obsługa kontekstów aktywacji w stanie modułu MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxstat_.h

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> Afxoleinitmodule —

Obsługę OLE od zwykłej biblioteki MFC DLL, która jest połączona dynamicznie z MFC, wywołaj tę funkcję w swojej zwykłej biblioteki MFC DLL w `CWinApp::InitInstance` funkcji, aby zainicjować biblioteki MFC DLL OLE.

### <a name="syntax"></a>Składnia

```
void AFXAPI AfxOleInitModule( );
```

### <a name="remarks"></a>Uwagi

Biblioteki MFC DLL OLE jest rozszerzeniem MFC DLL; w celu rozszerzenia MFC biblioteki DLL Pobierz połączonymi w `CDynLinkLibrary` łańcucha, należy utworzyć `CDynLinkLibrary` obiektu w kontekście każdego modułu, który będzie go używać. `AfxOleInitModule` Tworzy `CDynLinkLibrary` obiekt w kontekście swojej zwykłej biblioteki MFC DLL firmy, tak, aby go pobiera połączonymi w `CDynLinkLibrary` obiektu łańcucha zwykłej biblioteki MFC DLL.

Jeśli tworzysz kontrolkę OLE i korzystają `COleControlModule`, nie należy wywołać `AfxOleInitModule` ponieważ `InitInstance` funkcję członkowską `COleControlModule` wywołania `AfxOleInitModule`.

### <a name="requirements"></a>Wymagania

**Header**: \<afxdll_.h>

## <a name="afxnetinitmodule"></a>  AfxNetInitModule

Dla obsługi MFC gniazd od zwykłej biblioteki MFC DLL, która jest połączona dynamicznie z MFC, dodaj wywołanie tej funkcji w swojej zwykłej biblioteki MFC DLL w `CWinApp::InitInstance` funkcji, aby zainicjować biblioteki DLL MFC gniazd.

### <a name="syntax"></a>Składnia

```
void AFXAPI AfxNetInitModule( );
```

### <a name="remarks"></a>Uwagi

Biblioteki DLL MFC gniazd jest rozszerzeniem MFC DLL; w celu rozszerzenia MFC biblioteki DLL Pobierz połączonymi w `CDynLinkLibrary` łańcucha, należy utworzyć `CDynLinkLibrary` obiektu w kontekście każdego modułu, który będzie go używać. `AfxNetInitModule` Tworzy `CDynLinkLibrary` obiekt w kontekście swojej zwykłej biblioteki MFC DLL firmy, tak, aby go pobiera połączonymi w `CDynLinkLibrary` obiektu łańcucha zwykłej biblioteki MFC DLL.

### <a name="requirements"></a>Wymagania

**Header:** \<afxdll_.h>

## <a name="afxgetambientactctx"></a> AfxGetAmbientActCtx

Aby uzyskać bieżący stan flagi stanu-module, który ma wpływ na zachowanie folderze WinSxS MFC, należy użyć tej funkcji.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxGetAmbientActCtx();
```

### <a name="return-value"></a>Wartość zwracana

Moduł stanu bieżąca wartość flagi.

### <a name="remarks"></a>Uwagi

Gdy flaga jest ustawiona (jest to ustawienie domyślne) i wątku przechodzi modułu MFC (zobacz [AFX_MANAGE_STATE](#afx_manage_state)), kontekst modułu została aktywowana.

Jeśli nie ustawiono flagi, kontekst modułu nie została aktywowana przy uruchamianiu.

Kontekst modułu jest określana na podstawie jego manifestu, zwykle osadzone w module zasobów.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxcomctl32.h

## <a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState

Wywołaj tę funkcję, aby ustawić stan modułu przed zainicjowaniem i/lub w celu przywrócenia poprzedniego stanu modułu po oczyszczaniu.

### <a name="syntax"></a>Składnia

```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `AFX_MODULE_STATE` struktury.

### <a name="remarks"></a>Uwagi

`AFX_MODULE_STATE` Struktura zawiera dane globalne dla modułu, oznacza to, że część stanu modułu, który jest przypisany lub zdjęte ze stosu.

Domyślnie MFC wykorzystuje uchwyt zasobów aplikacji głównej można załadować szablonu zasobów. Jeśli masz eksportowanych funkcji w bibliotece DLL, taki, który uruchamia okno dialogowe w bibliotece DLL, ten szablon rzeczywiście jest przechowywana w moduł biblioteki DLL. Musisz przełączyć stanu modułu na prawidłowy uchwyt do użycia. Można to zrobić, dodając następujący kod na początku funkcji:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));
```

Zamienia to bieżący stan modułu ze stanem zwróciło `AfxGetStaticModuleState` aż do końca bieżącego zakresu.

Aby uzyskać więcej informacji na temat Stany modułu i MFC, zobacz temat "Zarządzanie stanu danych z MFC — moduły" w [tworzenie nowych dokumentów, Windows i widoki](../creating-new-documents-windows-and-views.md) i [techniczne 58 Uwaga](../tn058-mfc-module-state-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxstat_.h

## <a name="afxinitextensionmodule"></a> Afxinitextensionmodule —

Wywołaj tę funkcję w rozszerzenia MFC biblioteki DLL w `DllMain` można zainicjować biblioteki DLL.

### <a name="syntax"></a>Składnia

```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );
```

### <a name="parameters"></a>Parametry

*state*<br/>
Odwołanie do [afx_extension_module — struktura](afx-extension-module-structure.md) strukturę, która będzie zawierać stanu modułu MFC DLL rozszerzenia po zainicjowaniu. Stan obejmuje kopiowanie obiektów klasy środowiska uruchomieniowego, które zostały zainicjowane przez rozszerzenia MFC biblioteki DLL jako część konstruowania normalnych obiektu statycznego wykonywane przed `DllMain` wprowadzeniu.

*hModule*<br/>
Uchwyt modułu biblioteki DLL rozszerzenia MFC.

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie zainicjowano biblioteki DLL rozszerzenia MFC; w przeciwnym razie wartość FALSE.

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

`AfxInitExtensionModule` Tworzy kopię HMODULE biblioteki DLL i przechwytuje klasy środowiska wykonawczego bibliotek DLL (`CRuntimeClass` struktury) oraz jego obiekt fabryki (`COleObjectFactory` obiektów) do użycia po późniejszym `CDynLinkLibrary` obiekt zostanie utworzony.
Rozszerzenia MFC biblioteki DLL trzeba wykonać dwie czynności w ich `DllMain` funkcji:

- Wywołaj [afxinitextensionmodule —](#_mfc_afxinitextensionmodule) i sprawdź wartość zwracaną.

- Tworzenie `CDynLinkLibrary` obiektu, jeśli biblioteka DLL będzie eksportowanie [struktura CRuntimeClass](cruntimeclass-structure.md) obiektów lub ma swoje własne niestandardowe zasoby.

Możesz wywołać `AfxTermExtensionModule` oczyszczania podczas każdego procesu odłączy się od rozszerzenia MFC biblioteki DLL rozszerzenia MFC biblioteki DLL (której się dzieje, gdy kończy proces lub zwalnianie biblioteki DLL na `AfxFreeLibrary` wywołania).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdll_.h

## <a name="afxsetambientactctx"></a>  AfxSetAmbientActCtx

Ta funkcja służy do ustawiania flagi stanu-module, który ma wpływ na zachowanie folderze WinSxS MFC.

### <a name="syntax"></a>Składnia

```
void AFXAPI AfxSetAmbientActCtx(BOOL bSet);
```

### <a name="parameters"></a>Parametry

*bUstawienie*<br/>
Nowa wartość flagi stanu modułu.

### <a name="remarks"></a>Uwagi

Gdy flaga jest ustawiona (jest to ustawienie domyślne) i wątku przechodzi modułu MFC (zobacz [AFX_MANAGE_STATE](#afx_manage_state)), kontekst modułu została aktywowana.
Jeśli nie ustawiono flagi, kontekst modułu nie została aktywowana przy uruchamianiu.
Kontekst modułu jest określana na podstawie jego manifestu, zwykle osadzone w module zasobów.

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

## <a name="afxtermextensionmodule"></a>  Afxtermextensionmodule —

Wywołaj tę funkcję, aby umożliwić MFC do oczyszczania biblioteki DLL rozszerzenia MFC podczas każdego procesu odłączy się od biblioteki DLL (której się dzieje, gdy kończy proces lub zwalnianie biblioteki DLL na `AfxFreeLibrary` wywołania).

### <a name="syntax"></a>Składnia

```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );
```

### <a name="parameters"></a>Parametry

*state*<br/>
Odwołanie do [afx_extension_module —](afx-extension-module-structure.md) struktury, który zawiera stan modułu biblioteki DLL rozszerzenia MFC.

*Piłka*<br/>
Jeśli PRAWDA, wyczyść wszystkie moduły biblioteki DLL rozszerzeń MFC. W przeciwnym razie Oczyszczanie tylko bieżący moduł biblioteki DLL.

### <a name="remarks"></a>Uwagi

`AfxTermExtensionModule` Spowoduje to usunąć wszelkie lokalny magazyn dołączony do modułu i usunąć wszystkie wpisy z pamięci podręcznej mapy wiadomości. Na przykład:

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

Jeśli aplikacja ładuje i zwalnia dynamicznie biblioteki DLL rozszerzeń MFC, należy wywołać `AfxTermExtensionModule`. Ponieważ większość rozszerzenia MFC biblioteki DLL nie są ładowane dynamicznie (zazwyczaj są połączone za pośrednictwem ich bibliotekami importowanymi), wywołanie `AfxTermExtensionModule` zazwyczaj nie jest konieczne.

Rozszerzenia MFC biblioteki DLL należy wywołać [afxinitextensionmodule —](#afxinitextensionmodule) w ich `DllMain`. Jeśli eksportu biblioteki DLL [CRuntimeClass](cruntimeclass-structure.md) obiektów lub ma swoje własne niestandardowe zasoby, należy także utworzyć `CDynLinkLibrary` obiektu `DllMain`.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdll_.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)<br/>
[Zarządzanie danymi stanu modułów MFC](../managing-the-state-data-of-mfc-modules.md)<br/>
