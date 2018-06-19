---
title: Coleobjectfactory — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd68493c9be5eb0bff63504cf49b38b9a2f216d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375940"
---
# <a name="coleobjectfactory-class"></a>Coleobjectfactory — klasa
Implementuje OLE klasy factory, które tworzy obiektów OLE, takich jak serwery, obiekty automatyzacji i dokumenty.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Konstruuje `COleObjectFactory` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleObjectFactory::GetClassID](#getclassid)|Identyfikator obiekty, które tworzy tej fabryki klasy zwraca OLE.|  
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Określa, czy licencji formantu jest prawidłowy.|  
|[COleObjectFactory::IsRegistered](#isregistered)|Wskazuje, czy fabryka obiektu jest zarejestrowana w systemie OLE biblioteki dll.|  
|[COleObjectFactory::Register](#register)|Rejestruje fabrykę tego obiektu w systemie OLE biblioteki dll.|  
|[COleObjectFactory::RegisterAll](#registerall)|Rejestruje wszystkie aplikacji, fabryki obiektu OLE systemowej biblioteki dll.|  
|[COleObjectFactory::Revoke](#revoke)|Wycofanie tej fabryki obiektu rejestracji w systemie OLE biblioteki dll.|  
|[COleObjectFactory::RevokeAll](#revokeall)|Wycofanie rejestracje fabryki obiekt aplikacji w systemie OLE biblioteki dll.|  
|[COleObjectFactory::UnregisterAll](#unregisterall)|Wyrejestrowuje wszystkie fabryk obiektu aplikacji.|  
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Rejestruje fabrykę tego obiektu z rejestru systemowego OLE.|  
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Rejestruje wszystkie fabryk obiektu aplikacji z rejestru systemowego OLE.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Żąda Unikatowy klucz z biblioteki DLL formantu.|  
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Wywoływane przez platformę, by utworzyć nowy obiekt typu tej fabryki.|  
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Sprawdza, czy klucz osadzony w formancie odpowiada klucz osadzone w kontenerze.|  
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Sprawdza, czy formant jest licencjonowany do użytku w czasie projektowania.|  
  
## <a name="remarks"></a>Uwagi  
 `COleObjectFactory` Klasa ma funkcje elementów członkowskich do wykonywania następujących funkcji:  
  
-   Zarządzanie rejestracji obiektów.  
  
-   Aktualizowanie rejestru systemu OLE, a także rejestracji środowiska wykonawczego, które informują OLE, czy obiekty są uruchomione i gotowe do odbierania wiadomości.  
  
-   Wymuszanie licencjonowania ograniczając sterowaniu deweloperom licencjonowanych w czasie projektowania i licencjonowanych aplikacji w czasie wykonywania.  
  
-   Zarejestrowanie fabryki obiekt formantu z rejestru systemowego OLE.  
  
 Aby uzyskać więcej informacji dotyczących tworzenia obiektów, zobacz artykuły [obiekty danych i źródła danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md) i [obiekty danych i źródła danych: tworzenie i likwidacja](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Aby uzyskać więcej informacji o rejestracji, zobacz artykuł [rejestracji](../../mfc/registration.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory  
 Konstruuje `COleObjectFactory` obiekt, inicjuje go jako fabrykę obiektu wyrejestrować i dodaje go do listy fabryk.  
  
```  
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    LPCTSTR lpszProgID);

 
COleObjectFactory(
    REFCLSID clsid,  
    CRuntimeClass* pRuntimeClass,  
    BOOL bMultiInstance,  
    int nFlags,  
    LPCTSTR lpszProgID);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Reprezentuje odwołanie do Identyfikatora klasy OLE fabryki tego obiektu.  
  
 `pRuntimeClass`  
 Wskaźnik do klasy środowiska wykonawczego obiektów C++, których można utworzyć tej fabryki.  
  
 `bMultiInstance`  
 Wskazuje, czy pojedyncze wystąpienie aplikacji może obsługiwać wiele wystąpień. Jeśli **TRUE**, wiele wystąpień aplikacji będą uruchamiane dla każdego żądania do utworzenia obiektu.  
  
 `nFlags`  
 Zawiera co najmniej jeden z następujących flag:  
  
- **afxRegDefault** ThreadingModel ustawia model wątkowości typu Apartment =.  
  
- **afxreginsertable —** umożliwia sterowanie pojawią się w **Wstaw obiekt** okno dialogowe dla obiektów OLE.  
  
- `afxRegApartmentThreading` Ustawia model wątkowości w rejestrze ThreadingModel = apartamentu.  
  
- **afxregfreethreading —** ustawia model wątkowości w rejestrze ThreadingModel = wolne.  
  
     Możesz połączyć ze sobą dwie flagi `afxRegApartmentThreading` i `afxRegFreeThreading` można ustawić ThreadingModel = jednocześnie. Zobacz [InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390) w zestawie SDK systemu Windows, aby uzyskać więcej informacji o rejestracji modelu wątkowości.  
  
 `lpszProgID`  
 Wskaźnik do ciąg zawierający identyfikator ustne programu, takie jak "Microsoft Excel."  
  
### <a name="remarks"></a>Uwagi  
 Aby użyć obiektu, jednak musi być zarejestrowany.  
  
 Aby uzyskać więcej informacji, zobacz [klucz CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) w zestawie Windows SDK.  
  
##  <a name="getclassid"></a>  COleObjectFactory::GetClassID  
 Zwraca odwołanie do Identyfikatora klasy OLE reprezentuje tej fabryki.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Reprezentuje odwołanie do Identyfikatora klasy OLE tej fabryki.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [klucz CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) w zestawie Windows SDK.  
  
##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey  
 Żąda licencji Unikatowy klucz z biblioteki DLL formantu i przechowuje ją w `BSTR` wskazywana przez `pbstrKey`.  
  
```  
virtual BOOL GetLicenseKey(
    DWORD dwReserved,  
    BSTR* pbstrKey);
```  
  
### <a name="parameters"></a>Parametry  
 `dwReserved`  
 Zarezerwowane do użytku w przyszłości.  
  
 `pbstrKey`  
 Wskaźnik do `BSTR` którym będzie przechowywany klucz licencji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ciąg klucza licencji nie jest **NULL**; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja ta funkcja zwraca wartość 0 i przechowuje postanowienia `BSTR`. Jeśli używasz MFC ActiveX ControlWizard do tworzenia projektu ControlWizard dostarcza przesłonięcie pobiera klucz licencji formantu.  
  
##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid  
 Określa, czy licencji formantu jest prawidłowy.  
  
```  
BOOL IsLicenseValid();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli powiodła; w przeciwnym razie wartość false.  
  
##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered  
 Zwraca wartość niezerową, jeśli fabryka jest zarejestrowany w systemie OLE biblioteki dll.  
  
```  
virtual BOOL IsRegistered() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli fabryka jest zarejestrowany; w przeciwnym razie 0.  
  
##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject  
 Wywoływane przez platformę, by utworzyć nowy obiekt.  
  
```  
virtual CCmdTarget* OnCreateObject();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do utworzonego obiektu. Go zgłosić wyjątek pamięci, jeśli działanie nie powiodło się.  
  
### <a name="remarks"></a>Uwagi  
 Zastąpienie tej funkcji można utworzyć obiektu z coś innego niż [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) przekazany do konstruktora.  
  
##  <a name="register"></a>  COleObjectFactory::Register  
 Rejestruje fabrykę tego obiektu w systemie OLE biblioteki dll.  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli zostanie pomyślnie zarejestrowana fabryka; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.  
  
##  <a name="registerall"></a>  COleObjectFactory::RegisterAll  
 Rejestruje wszystkie fabryk obiekt aplikacji w systemie OLE biblioteki dll.  
  
```  
static BOOL PASCAL RegisterAll();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pomyślnie zostały zarejestrowane fabryk; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.  
  
##  <a name="revoke"></a>  COleObjectFactory::Revoke  
 Wycofanie tej fabryki obiektu rejestracji w systemie OLE biblioteki dll.  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Uwagi  
 Struktura automatycznie wywołuje tej funkcji, zanim zakończy aplikacji. W razie potrzeby wywołać ją z zastępująca [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll  
 Odwołuje wszystkie rejestracje fabryki obiekt aplikacji w systemie OLE biblioteki dll.  
  
```  
static void PASCAL RevokeAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Struktura automatycznie wywołuje tej funkcji, zanim zakończy aplikacji. W razie potrzeby wywołać ją z zastępująca [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).  
  
##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll  
 Wyrejestrowuje wszystkie fabryk obiektu aplikacji.  
  
```  
static BOOL PASCAL UnregisterAll();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślnie; w przeciwnym razie wartość FALSE.  
  
##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry  
 Rejestruje wszystkie fabryk obiektu aplikacji z rejestru systemowego OLE.  
  
```  
void UpdateRegistry(LPCTSTR lpszProgID = NULL);  
virtual BOOL UpdateRegistry(BOOL bRegister);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszProgID`  
 Wskaźnik do ciąg zawierający identyfikator programu zrozumiałą dla użytkownika, takie jak "Excel.Document.5."  
  
 `bRegister`  
 Określa, czy fabrykę obiektów klasy formantu ma zostać zarejestrowany.  
  
### <a name="remarks"></a>Uwagi  
 Wykonaj krótkie omówienie dwa formularze dla tej funkcji:  
  
- **UpdateRegistry (** `lpszProgID` **)** rejestruje fabrykę tego obiektu z rejestru systemowego OLE. Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.  
  
- **UpdateRegistry (** `bRegister` **)** ten formularz funkcji jest możliwym do zastąpienia. Jeśli `bRegister` jest **TRUE**, ta funkcja rejestruje klasy formantu z rejestru systemowego. W przeciwnym razie go wyrejestrowuje klasy.  
  
     Jeśli używasz MFC ActiveX ControlWizard do tworzenia projektu ControlWizard dostarcza zastąpienie tego czystej funkcji wirtualnej.  
  
##  <a name="updateregistryall"></a>  COleObjectFactory::UpdateRegistryAll  
 Rejestruje wszystkie fabryk obiektu aplikacji z rejestru systemowego OLE.  
  
```  
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bRegister`  
 Określa, czy fabrykę obiektów klasy formantu ma zostać zarejestrowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pomyślnie zostały zaktualizowane fabryk; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.  
  
##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey  
 Sprawdza, czy kontener jest licencji na korzystanie z formantu OLE.  
  
```  
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrKey`  
 A `BSTR` przechowywania wersji kontenera ciągu licencji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli licencji jest nieprawidłowy; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania wersji domyślnej [GetLicenseKey](#getlicensekey) uzyskać kopię formantu ciąg licencji użytkownika i porównuje ją z ciągiem w `bstrKey`. Jeśli dwa ciągi zgodne, funkcja zwraca wartość niezerową; w przeciwnym razie zwraca wartość 0.  
  
 Można zastąpić tę funkcję, aby zapewnić dostosowane weryfikację licencji.  
  
 Funkcja [VerifyUserLicense](#verifyuserlicense) sprawdza licencji czasu projektowania.  
  
##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense  
 Sprawdza, czy licencji czasu projektowania formantu OLE.  
  
```  
virtual BOOL VerifyUserLicense();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli licencji jest nieprawidłowy; w przeciwnym razie 0.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
