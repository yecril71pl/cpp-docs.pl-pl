---
title: Makra i funkcje do zarządzania biblioteki dll | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- module macros in MFC
ms.assetid: 303f4161-cb5e-4099-81ad-acdb11aa60fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5e79556bf6e3ae92f7a8d4975dbd30f199e2ca8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376479"
---
# <a name="macros-and-functions-for-managing-dlls"></a>Makra i funkcje do zarządzania bibliotek DLL

|||
|-|-|
|[AFX_EXT_CLASS —](#afx_ext_class)]|Eksportuje klasy.|
|[AFX_MANAGE_STATE —](#afx_manage_state)|Ochrona wyeksportowanych funkcji w bibliotece DLL.|
|[Afxoleinitmodule —](#afxoleinitmodule)|Zapewnia obsługę OLE z regularne biblioteki DLL MFC, która jest połączona dynamicznie z MFC.|
|[Afxnetinitmodule —](#afxnetinitmodule)|Umożliwia obsługę MFC gniazda z regularne biblioteki DLL MFC, która jest połączona dynamicznie z MFC.|
|[Afxgetambientactctx —](#afxgetambientactctx)|Pobiera bieżący stan flagi stanu-module.|
|[AfxGetStaticModuleState —](#afxgetstaticmodulestate)|Ustawia stan modułu przed zainicjowaniem i/lub przywrócić poprzedniego stanu modułu po oczyszczania.|
|[Afxinitextensionmodule —]()#afxinitextensionmodule|Inicjuje biblioteki DLL.|
|[Afxsetambientactctx —](#afxsetambientactctx)|Ustaw wartość flagi stanu-module, który ma wpływ na zachowanie folderze WinSxS MFC.|
|[Afxtermextensionmodule —]()#afxtermextensionmodule)|Umożliwia MFC do oczyszczania bibliotekę DLL rozszerzenia MFC podczas każdego procesu odłącza z biblioteki DLL.|


## <a name="afx_ext_class"></a>  AFX_EXT_CLASS —
[Biblioteki DLL rozszerzeń MFC](../../build/extension-dlls.md) użyć makra **afx_ext_class —** Aby wyeksportować klasy, plików wykonywalnych, które łącze do biblioteki DLL rozszerzenia MFC przy użyciu makra można zaimportować klas.  
   
### <a name="remarks"></a>Uwagi  
 Z **afx_ext_class —** makra, ten sam nagłówek plików używany do tworzenia biblioteki DLL rozszerzenia MFC mogą być używane z plików wykonywalnych, które łącze do pliku DLL.  
  
 W pliku nagłówka dla biblioteki DLL, Dodaj **afx_ext_class —** — słowo kluczowe do deklaracji klasy w następujący sposób:  
  
```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
``` 
  
 Aby uzyskać więcej informacji, zobacz [eksportu i importu za pomocą w afx_ext_class —](../../build/exporting-and-importing-using-afx-ext-class.md).  
   
### <a name="requirements"></a>Wymagania  
 Nagłówek: **afxv_** dll.h  
   
## <a name="afx_manage_state"></a>  AFX_MANAGE_STATE —
Wywołanie to makro, aby chronić wyeksportowanej funkcji w bibliotece DLL.  
   
### <a name="syntax"></a>Składnia    
```
AFX_MANAGE_STATE(AFX_MODULE_STATE* pModuleState )  
```
### <a name="parameters"></a>Parametry  
 `pModuleState`  
 Wskaźnik do `AFX_MODULE_STATE` struktury.  
   
### <a name="remarks"></a>Uwagi  
 Po wywołaniu to makro `pModuleState` jest skuteczne moduł stanu dla pozostałych natychmiastowego zawierający zakres. Opuszczających zakresu poprzedniego stanu modułu skuteczne zostanie automatycznie przywrócony.    
 `AFX_MODULE_STATE` Struktura zawiera dane globalne dla modułu, oznacza to, że część stan modułu, w którym jest naciśnięty, czy zdjęte ze stosu.    
 Domyślnie MFC używa zasobów dojście aplikacji głównej do załadowania szablonu zasobów. Jeśli wyeksportowanej funkcji DLL, który uruchamia okno dialogowe w bibliotece DLL, ten szablon faktycznie jest przechowywany w DLL module. Musisz przełączyć stan modułu na prawidłowe dojście do użycia. Można to zrobić przez dodanie poniższego kodu do początku funkcji:    
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
 Zamienia to bieżący stan modułu ze stanem zwrócony z [AfxGetStaticModuleState —](#afxgetstaticmodulestate) do końca bieżącego zakresu.    
 Aby uzyskać więcej informacji na stany modułów i MFC, zobacz "Zarządzanie stanu danych z MFC moduły" w [tworzenie nowych dokumentów, okien i widoków](../creating-new-documents-windows-and-views.md) i [58 Uwaga techniczna](../tn058-mfc-module-state-implementation.md).    
> [!NOTE]
>  Gdy MFC tworzy kontekst aktywacji dla zestawu, używa [afxwininit —](#afxwininit) można utworzyć kontekstu i `AFX_MANAGE_STATE` na aktywowanie i dezaktywowanie go. Należy zauważyć, że `AFX_MANAGE_STATE` jest włączona dla statycznych biblioteki MFC, jak również biblioteki DLL MFC, aby umożliwić kod wykonywany w kontekście prawidłowego aktywacji wybrane przez użytkownika biblioteki DLL MFC. Aby uzyskać więcej informacji, zobacz [Obsługa kontekstów aktywacji w stanie modułu MFC](../support-for-activation-contexts-in-the-mfc-module-state.md).     
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxstat_.h  
   
### <a name="see-also"></a>Zobacz też  
 [AfxGetStaticModuleState —](#afxgetstaticmodulestate)

## <a name="a-nameafxoleinitmodulea-afxoleinitmodule"></a><a name="afxoleinitmodule"><a/> Afxoleinitmodule —
Obsługa OLE z regularne biblioteki DLL MFC, która jest połączona dynamicznie z MFC wywołanie tej funkcji w bibliotece regularne DLL MFC `CWinApp::InitInstance` funkcji, aby zainicjować biblioteki MFC DLL OLE.  
   
### <a name="syntax"></a>Składnia    
```
void AFXAPI AfxOleInitModule( );  
```  
   
### <a name="remarks"></a>Uwagi  
 Biblioteki MFC DLL OLE jest rozszerzeniem MFC DLL; w celu rozszerzenia MFC DLL uzyskać przewodowej do **CDynLinkLibrary** łańcucha, należy utworzyć **CDynLinkLibrary** obiektu w kontekście każdy moduł, który będzie go używać. `AfxOleInitModule` Tworzy **CDynLinkLibrary** obiekt w kontekście użytkownika regularne DLL MFC, tak aby pobiera ona przewodowej do **CDynLinkLibrary** obiekt łańcucha regularne biblioteki DLL MFC.  
  
 Jeśli budowania kontrolkę OLE i korzystają z `COleControlModule`, nie należy wywołać **afxoleinitmodule —** ponieważ `InitInstance` funkcji członkowskiej dla `COleControlModule` wywołania `AfxOleInitModule`.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek**: < afxdll_.h >  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxnetinitmodule"></a>  Afxnetinitmodule —
Obsługuje gniazda MFC z regularne biblioteki DLL MFC, która jest połączona dynamicznie z MFC, dodaj wywołanie tej funkcji w bibliotece regularne DLL MFC **CWinApp::InitInstance** funkcji, aby zainicjować biblioteki gniazd MFC DLL.  
   
### <a name="syntax"></a>Składnia    
```
void AFXAPI AfxNetInitModule( );  
```  
   
### <a name="remarks"></a>Uwagi  
 MFC DLL gniazd jest rozszerzenie MFC DLL; w celu rozszerzenia MFC DLL uzyskać przewodowej do **CDynLinkLibrary** łańcucha, należy utworzyć **CDynLinkLibrary** obiektu w kontekście każdy moduł, który będzie go używać. `AfxNetInitModule` Tworzy **CDynLinkLibrary** obiekt w kontekście użytkownika regularne DLL MFC, tak aby pobiera ona przewodowej do **CDynLinkLibrary** obiekt łańcucha regularne biblioteki DLL MFC.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** < afxdll_.h >  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)

## <a name="afxgetambientactctx"></a> Afxgetambientactctx —
Ta funkcja umożliwia pobieranie bieżącego stanu flagi stanu-module, który ma wpływ na zachowanie folderze WinSxS MFC.  
   
### <a name="syntax"></a>Składnia    
```  
BOOL AFXAPI AfxGetAmbientActCtx();   
```  
   
### <a name="return-value"></a>Wartość zwracana  
 Moduł stanu flagi bieżącą wartość.  
   
### <a name="remarks"></a>Uwagi  
 Jeśli flaga jest ustawiona (która jest wartością domyślną) i wątku wprowadzenia modułu MFC (zobacz [afx_manage_state —](#afx_manage_state)), kontekst modułu jest aktywny.  
  
 Jeśli nie ustawiono flagi, kontekst modułu nie została aktywowana w wpis.  
  
 Kontekst modułu jest określana na podstawie swoim manifeście zwykle osadzone w module zasobów.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcomctl32.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [AFX_MANAGE_STATE —](#afx_manage_state)   
 [Zarządzanie danymi stanu modułów MFC](../managing-the-state-data-of-mfc-modules.md)   
 [Afxsetambientactctx —](#setambientactctx)
 
## <a name="afxgetstaticmodulestate"></a> AfxGetStaticModuleState —
Wywołanie tej funkcji, aby ustawić stan modułu przed zainicjowaniem i/lub przywrócić poprzedniego stanu modułu po oczyszczania.  
   
### <a name="syntax"></a>Składnia    
```
AFX_MODULE_STATE* AFXAPI AfxGetStaticModuleState( );  
```  
   
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `AFX_MODULE_STATE` struktury.  
   
### <a name="remarks"></a>Uwagi  
 `AFX_MODULE_STATE` Struktura zawiera dane globalne dla modułu, oznacza to, że część stan modułu, w którym jest naciśnięty, czy zdjęte ze stosu.  
  
 Domyślnie MFC używa zasobów dojście aplikacji głównej do załadowania szablonu zasobów. Jeśli wyeksportowanej funkcji DLL, który uruchamia okno dialogowe w bibliotece DLL, ten szablon faktycznie jest przechowywany w DLL module. Musisz przełączyć stan modułu na prawidłowe dojście do użycia. Można to zrobić przez dodanie poniższego kodu do początku funkcji:  
  
```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState( ));

```
  
 Zamienia to bieżący stan modułu ze stanem zwrócony z `AfxGetStaticModuleState` do końca bieżącego zakresu.  
  
 Aby uzyskać więcej informacji na stany modułów i MFC, zobacz "Zarządzanie stanu danych z MFC moduły" w [tworzenie nowych dokumentów, okien i widoków](../creating-new-documents-windows-and-views.md) i [58 Uwaga techniczna](../tn058-mfc-module-state-implementation.md).  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxstat_.h  
   

## <a name="afxinitextensionmodule"></a> Afxinitextensionmodule —
Wywołanie tej funkcji w MFC DLL rozszerzenia w `DllMain` zainicjować biblioteki DLL.  
   
### <a name="syntax"></a>Składnia    
```
BOOL AFXAPI AfxInitExtensionModule( AFX_EXTENSION_MODULE& state,  HMODULE hModule );  
```
### <a name="parameters"></a>Parametry  
 `state`  
 Odwołanie do [afx_extension_module — struktura](afx-extension-module-structure.md) strukturę, która będzie zawierać stanu modułu MFC DLL rozszerzenia po zainicjowaniu. Stan zawiera kopię obiektów klasy środowiska uruchomieniowego, które zostały zainicjowane przez bibliotekę DLL rozszerzenia MFC jako część konstrukcji obiektu statycznego normalne wykonywany przed `DllMain` została wprowadzona.  
  
 `hModule`  
 Uchwyt modułu DLL rozszerzenia MFC.  
   
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** w przypadku biblioteki DLL rozszerzenia MFC pomyślnie zainicjowane, a w przeciwnym razie **FALSE**.  
   
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

```
  
 `AfxInitExtensionModule` Tworzy kopię pliku DLL **HMODULE** i przechwytywanie DLL środowiska uruchomieniowego klasy (`CRuntimeClass` struktury) oraz jego fabryk obiektu (`COleObjectFactory` obiektów) do użycia w przypadku nowszych **CDynLinkLibrary**tworzony jest obiekt.    
 Rozszerzenia MFC DLL należy wykonać dwie czynności w ich `DllMain` funkcji:    
-   Wywołanie [afxinitextensionmodule —](#_mfc_afxinitextensionmodule) i sprawdzić wartość zwrotną.   
-   Utwórz **CDynLinkLibrary** obiektu, jeśli zostanie wyeksportowany plik DLL [struktury CRuntimeClass](cruntimeclass-structure.md) obiektów lub ma własne niestandardowe zasoby.    
 Możesz wywołać `AfxTermExtensionModule` oczyszczania podczas każdego procesu odłącza z biblioteki DLL rozszerzenia MFC DLL rozszerzenia MFC (które ma miejsce, gdy kończy proces lub gdy biblioteka DLL jest zwalnianie w `AfxFreeLibrary` wywołania).     

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdll_.h     

### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Afxtermextensionmodule —](#afxtermextensionmodule)

 ## <a name="afxsetambientactctx"></a>  Afxsetambientactctx —
Użyj tej funkcji można ustawić flagi stanu-module, który ma wpływ na zachowanie folderze WinSxS MFC.  
   
### <a name="syntax"></a>Składnia  
  ```
   void AFXAPI AfxSetAmbientActCtx( BOOL bSet  
);  
```
### <a name="parameters"></a>Parametry  
 `bSet`  
 Nowa wartość flagi stanu modułu.  
   
### <a name="remarks"></a>Uwagi  
 Jeśli flaga jest ustawiona (która jest wartością domyślną) i wątku wprowadzenia modułu MFC (zobacz [afx_manage_state —](#afx_manage_state)), kontekst modułu jest aktywny.    
 Jeśli nie ustawiono flagi, kontekst modułu nie została aktywowana w wpis.    
 Kontekst modułu jest określana na podstawie swoim manifeście zwykle osadzone w module zasobów.  
   
### <a name="example"></a>Przykład  
 ```cpp
BOOL CMFCListViewApp::InitInstance()
{
   AfxSetAmbientActCtx(FALSE);
   // Remainder of function definition omitted.
```
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxcomctl32.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Afxgetambientactctx —](#afxgetambientactctx)   
 [AFX_MANAGE_STATE —](#afx_manage_state)   
 [Zarządzanie danymi stanu modułów MFC](../managing-the-state-data-of-mfc-modules.md) 

## <a name="afxtermextensionmodule"></a>  Afxtermextensionmodule —

Wywołanie tej funkcji, aby umożliwić MFC do oczyszczania bibliotekę DLL rozszerzenia MFC podczas każdego procesu odłącza z biblioteki DLL (które ma miejsce, gdy kończy proces lub gdy biblioteka DLL jest zwalnianie w `AfxFreeLibrary` wywołania).  
   
### <a name="syntax"></a>Składnia  
  ```
void AFXAPI AfxTermExtensionModule(  AFX_EXTENSION_MODULE& state,  BOOL bAll  = FALSE );  
```
### <a name="parameters"></a>Parametry  
 `state`  
 Odwołanie do [afx_extension_module —](afx-extension-module-structure.md) struktury, który zawiera stan modułu DLL rozszerzenia MFC.  
  
 *Piłka*  
 Jeśli **TRUE**, oczyścić wszystkie moduły biblioteki DLL rozszerzenia MFC. W przeciwnym razie czyszczenia tylko bieżącego modułu biblioteki DLL.  
   
### <a name="remarks"></a>Uwagi  
 `AfxTermExtensionModule` Spowoduje to usunięcie wszelkich lokalny magazyn dołączony do modułu i usunąć wszystkie wpisy z pamięci podręcznej mapy wiadomości. Na przykład:  
  
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
  
 Jeśli aplikacja ładuje i zwalnia dynamicznie biblioteki DLL rozszerzeń MFC, należy wywołać `AfxTermExtensionModule`. Ponieważ większość rozszerzenia MFC DLL nie są ładowane dynamicznie (zazwyczaj są powiązane za pośrednictwem ich bibliotekami importowanymi), wywołanie `AfxTermExtensionModule` zazwyczaj nie jest konieczne.  
  
 Rozszerzenia MFC DLL musi wywołać [afxinitextensionmodule —](#afxinitextensionmodule) w ich `DllMain`. Jeśli zostanie wyeksportowany plik DLL [CRuntimeClass](cruntimeclass-structure.md) obiektów lub ma własne niestandardowe zasoby, należy także utworzyć **CDynLinkLibrary** obiektu w `DllMain`.  
   
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdll_.h  
   
### <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](mfc-macros-and-globals.md)   
 [Afxinitextensionmodule —](#afxinitextensionmodule)
 




