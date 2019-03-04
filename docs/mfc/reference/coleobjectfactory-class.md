---
title: Coleobjectfactory — klasa
ms.date: 11/04/2016
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
ms.openlocfilehash: 25dce92f49ba9de08fcf33d54db8e97d520f5ea4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266383"
---
# <a name="coleobjectfactory-class"></a>Coleobjectfactory — klasa

Implementuje mechanizm klasy OLE factory, która tworzy obiekty OLE, takich jak serwery, obiekty automatyzacji i dokumenty.

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
|[COleObjectFactory::GetClassID](#getclassid)|Identyfikator obiekty, które tworzy tę fabrykę klasy zwraca OLE.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Określa, czy licencja formant jest prawidłowy.|
|[COleObjectFactory::IsRegistered](#isregistered)|Wskazuje, czy fabryki obiektów jest zarejestrowany w systemie OLE biblioteki dll.|
|[COleObjectFactory::Register](#register)|Rejestruje tę fabrykę obiektu OLE systemowych bibliotek DLL.|
|[COleObjectFactory::RegisterAll](#registerall)|Rejestruje wszystkie fabryki obiektów w aplikacji OLE systemowych bibliotek DLL.|
|[COleObjectFactory::Revoke](#revoke)|Odwołuje rejestracji tej fabryki obiektów OLE systemowych bibliotek DLL.|
|[COleObjectFactory::RevokeAll](#revokeall)|Odwołuje fabryk obiekt aplikacji rejestracji w systemie OLE biblioteki dll.|
|[COleObjectFactory::UnregisterAll](#unregisterall)|Wyrejestrowuje wszystkich fabryk obiektu aplikacji.|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Rejestruje tę fabrykę obiektu z rejestru systemowego OLE.|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Rejestruje wszystkie fabryki obiekt aplikacji z rejestru systemowego OLE.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Żąda Unikatowy klucz z formantu biblioteki DLL.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Metoda wywoływana przez platformę, by utworzyć nowy obiekt typu tej fabryki.|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Sprawdza, czy klucz osadzone w kontrolce odpowiada klucz osadzone w kontenerze.|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Sprawdza, czy kontrolka jest licencjonowany do użycia w czasie projektowania.|

## <a name="remarks"></a>Uwagi

`COleObjectFactory` Klasa ma funkcje Członkowskie do wykonywania następujących funkcji:

- Zarządzanie rejestracji obiektów.

- Aktualizowanie rejestru systemu OLE, a także rejestracji środowiska wykonawczego, które informują OLE, czy obiekty są uruchomione i gotowe do odbierania komunikatów.

- Wymuszanie licencjonowania, ograniczając sterowaniu licencjonowane deweloperom w czasie projektowania i licencjonowanych aplikacji w czasie wykonywania.

- Rejestrowanie sterowania obiekt fabryki z rejestru systemowego OLE.

Aby uzyskać więcej informacji na temat tworzenia obiektu, zobacz artykuły [obiekty danych i źródeł danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md) i [obiekty danych i źródeł danych: Tworzenie i likwidacja](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Aby uzyskać więcej informacji o rejestracji, zobacz artykuł [rejestracji](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

##  <a name="coleobjectfactory"></a>  COleObjectFactory::COleObjectFactory

Konstruuje `COleObjectFactory` obiektu, inicjuje go jako fabrykę obiektu niezarejestrowane i dodaje go do listy fabryk.

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

*Identyfikator klasy*<br/>
Reprezentuje odwołanie do Identyfikatora klasy OLE tej fabryki obiektów.

*pRuntimeClass*<br/>
Wskaźnik do klasy środowiska wykonawczego obiektów C++, których można utworzyć tej fabryki.

*bMultiInstance*<br/>
Wskazuje, czy pojedyncze wystąpienie aplikacji może obsługiwać wiele wystąpień. W przypadku wartości TRUE dla każdego żądania utworzyć obiekt uruchomienia wielu wystąpień aplikacji.

*nFlags*<br/>
Zawiera co najmniej jeden z następujących flag:

- `afxRegDefault` Ustawia ThreadingModel model wątkowości typu Apartment =.

- `afxRegInsertable` Zapewnia kontrolę pojawią się w **Wstawianie obiektu** okno dialogowe dla obiektów OLE.

- `afxRegApartmentThreading` Ustawia model wątkowości w rejestrze, aby ThreadingModel = typu Apartment.

- `afxRegFreeThreading` Ustawia model wątkowości w rejestrze, aby ThreadingModel = bezpłatna.

   Można połączyć dwie flagi `afxRegApartmentThreading` i `afxRegFreeThreading` można ustawić ThreadingModel = jednocześnie. Zobacz [InprocServer32](/windows/desktop/com/inprocserver32) w zestawie SDK Windows, aby uzyskać więcej informacji na temat rejestracji modelu wątkowości.

*lpszProgID*<br/>
Wskaźnik do ciągu zawierającego identyfikator programu werbalne, takie jak "Programu Microsoft Excel."

### <a name="remarks"></a>Uwagi

Aby użyć obiektu, jednak należy zarejestrować go.

Aby uzyskać więcej informacji, zobacz [klucz identyfikator CLSID](/windows/desktop/com/clsid-key-hklm) w zestawie Windows SDK.

##  <a name="getclassid"></a>  COleObjectFactory::GetClassID

Zwraca odwołanie do Identyfikatora klasy OLE reprezentuje tej fabryki.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Wartość zwracana

Reprezentuje odwołanie do Identyfikatora klasy OLE tej fabryki.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [klucz identyfikator CLSID](/windows/desktop/com/clsid-key-hklm) w zestawie Windows SDK.

##  <a name="getlicensekey"></a>  COleObjectFactory::GetLicenseKey

Żąda klucz unikatową licencję z formantu biblioteki DLL i zapisuje go w BSTR wskazywany przez *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Zarezerwowane do użytku w przyszłości.

*pbstrKey*<br/>
Wskaźnik do BSTR, w którym przechowywany będzie klucz licencji.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli ciąg klucz licencji nie jest równa NULL; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja ta funkcja zwraca wartość 0 i zapisuje nic w BSTR. Jeśli używasz MFC ActiveX ControlWizard do tworzenia projektu ControlWizard dostarcza przesłonięcie, która pobiera klucz licencji formantu.

##  <a name="islicensevalid"></a>  COleObjectFactory::IsLicenseValid

Określa, czy licencja formant jest prawidłowy.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powiodła; w przeciwnym razie wartość false.

##  <a name="isregistered"></a>  COleObjectFactory::IsRegistered

Zwraca wartość różną od zera, jeśli fabryka jest zarejestrowany w systemie OLE biblioteki dll.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli fabryka jest zarejestrowany; w przeciwnym razie 0.

##  <a name="oncreateobject"></a>  COleObjectFactory::OnCreateObject

Metoda wywoływana przez platformę, by utworzyć nowy obiekt.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do utworzonego obiektu. Może ona zgłosić wyjątek pamięci, jeśli zakończy się niepowodzeniem.

### <a name="remarks"></a>Uwagi

Zastąp tę funkcję, aby utworzyć obiekt z coś innego niż [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) przekazany do konstruktora.

##  <a name="register"></a>  COleObjectFactory::Register

Rejestruje tę fabrykę obiektu OLE systemowych bibliotek DLL.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli fabryka po pomyślnym zarejestrowaniu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.

##  <a name="registerall"></a>  COleObjectFactory::RegisterAll

Rejestruje wszystkie fabryki obiektów w aplikacji OLE systemowych bibliotek DLL.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli pomyślnie zarejestrowano fabryk; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.

##  <a name="revoke"></a>  COleObjectFactory::Revoke

Odwołuje rejestracji tej fabryki obiektów OLE systemowych bibliotek DLL.

```
void Revoke();
```

### <a name="remarks"></a>Uwagi

Struktura automatycznie wywołuje tę funkcję, zanim aplikacja zakończy. Jeśli to konieczne, wywołać go z zastąpieniem [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="revokeall"></a>  COleObjectFactory::RevokeAll

Odwołuje wszystkie rejestracje fabryk obiekt aplikacji w systemie OLE biblioteki dll.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Uwagi

Struktura automatycznie wywołuje tę funkcję, zanim aplikacja zakończy. Jeśli to konieczne, wywołać go z zastąpieniem [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="unregisterall"></a>  COleObjectFactory::UnregisterAll

Wyrejestrowuje wszystkich fabryk obiektu aplikacji.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.

##  <a name="updateregistry"></a>  COleObjectFactory::UpdateRegistry

Rejestruje wszystkie fabryki obiekt aplikacji z rejestru systemowego OLE.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parametry

*lpszProgID*<br/>
Wskaźnik do ciągu zawierającego identyfikator programu czytelny dla człowieka, takie jak "Excel.Document.5."

*bRegister*<br/>
Określa, czy można zarejestrować fabryki obiektów klasy kontrolki.

### <a name="remarks"></a>Uwagi

Krótkie omówienie dwie formy dla tej funkcji należy wykonać:

- **UpdateRegistry (** `lpszProgID` **)** rejestruje tę fabrykę obiektu z rejestru systemowego OLE. Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.

- **UpdateRegistry (** `bRegister` **)** ten rodzaj funkcji jest możliwym do zastąpienia. Jeśli *bRegister* ma wartość PRAWDA, to rejestrów funkcja kontrolki klasy z rejestru systemowego. W przeciwnym razie wyrejestrowuje klasy.

   Jeśli używasz MFC ActiveX ControlWizard do tworzenia projektu ControlWizard dostarcza zastąpienie tego czystą funkcję wirtualną.

##  <a name="updateregistryall"></a>  COleObjectFactory::UpdateRegistryAll

Rejestruje wszystkie fabryki obiekt aplikacji z rejestru systemowego OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*bRegister*<br/>
Określa, czy można zarejestrować fabryki obiektów klasy kontrolki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli fabryk pomyślnie zostaną zaktualizowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.

##  <a name="verifylicensekey"></a>  COleObjectFactory::VerifyLicenseKey

Sprawdza, czy kontener jest licencji na korzystanie z kontrolki OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parametry

*bstrKey*<br/>
Ciąg BSTR przechowywania kontenera wersję ciągu licencji.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli licencja środowiska wykonawczego jest prawidłowy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołania wersja domyślna [getlicensekey —](#getlicensekey) uzyskać kopię kontrolki użytkownika ciągu licencji i porównuje ją z ciągu w *bstrKey*. Jeśli dwa ciągi są zgodne, funkcja zwraca wartość różną od zera; w przeciwnym razie zwraca wartość 0.

Można zastąpić tę funkcję, aby zapewnić dostosowane Weryfikacja licencji.

Funkcja [verifyuserlicense —](#verifyuserlicense) sprawdza licencji czasu projektowania.

##  <a name="verifyuserlicense"></a>  COleObjectFactory::VerifyUserLicense

Weryfikuje licencji czasu projektowania formantu OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli licencji czasu projektowania jest prawidłowy; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz także

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
