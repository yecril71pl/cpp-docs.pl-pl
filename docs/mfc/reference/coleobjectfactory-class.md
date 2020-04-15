---
title: Klasa COleObjectFactory
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
ms.openlocfilehash: 9f3d86cf735c02b6021441c66d9fd64547f6d6c2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374906"
---
# <a name="coleobjectfactory-class"></a>Klasa COleObjectFactory

Implementuje fabrykę klas OLE, która tworzy obiekty OLE, takie jak serwery, obiekty automatyzacji i dokumenty.

## <a name="syntax"></a>Składnia

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleObjectFactory::COleObjectFactory](#coleobjectfactory)|Konstruuje `COleObjectFactory` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleObjectFactory::GetClassID](#getclassid)|Zwraca identyfikator klasy OLE obiektów, które tworzy fabryka.|
|[COleObjectFactory::IsLicenseValid](#islicensevalid)|Określa, czy licencja formantu jest ważna.|
|[COleObjectFactory::JestReregistered](#isregistered)|Wskazuje, czy fabryka obiektów jest zarejestrowana w bibliotekach DLL systemu OLE.|
|[COleObjectFactory::Zarejestruj się](#register)|Rejestruje tę fabrykę obiektów za pomocą bibliotek DLL systemu OLE.|
|[COleObjectFactory::RegisterAll](#registerall)|Rejestruje wszystkie fabryki obiektów aplikacji za pomocą bibliotek DLL systemu OLE.|
|[COleObjectFactory::Odwołaj](#revoke)|Odwołuje rejestrację tej fabryki obiektów w bibliotekach DLL systemu OLE.|
|[COleObjectFactory::RevokeAll](#revokeall)|Odwołuje rejestracje obiektów aplikacji za pomocą bibliotek DLL systemu OLE.|
|[COleObjectFactory::WyrejestrowaćWszywszy](#unregisterall)|Wyrejestrowaj wszystkie fabryki obiektów aplikacji.|
|[COleObjectFactory::UpdateRegistry](#updateregistry)|Rejestruje tę fabrykę obiektów w rejestrze systemu OLE.|
|[COleObjectFactory::UpdateRegistryAll](#updateregistryall)|Rejestruje wszystkie fabryki obiektów aplikacji w rejestrze systemu OLE.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleObjectFactory::GetLicenseKey](#getlicensekey)|Żąda unikatowy klucz z biblioteki DLL formantu.|
|[COleObjectFactory::OnCreateObject](#oncreateobject)|Wywoływana przez strukturę, aby utworzyć nowy obiekt tego typu fabryki.|
|[COleObjectFactory::VerifyLicenseKey](#verifylicensekey)|Sprawdza, czy klucz osadzony w formancie pasuje do klucza osadzonego w kontenerze.|
|[COleObjectFactory::VerifyUserLicense](#verifyuserlicense)|Sprawdza, czy formant jest licencjonowany do użycia w czasie projektowania.|

## <a name="remarks"></a>Uwagi

Klasa `COleObjectFactory` ma funkcje członkowskie do wykonywania następujących funkcji:

- Zarządzanie rejestracją obiektów.

- Aktualizowanie rejestru systemu OLE, a także rejestracji w czasie wykonywania, która informuje OLE, że obiekty są uruchomione i gotowe do odbierania wiadomości.

- Wymuszanie licencjonowania przez ograniczenie użycia formantu do licencjonowanych deweloperów w czasie projektowania i licencjonowanych aplikacji w czasie wykonywania.

- Rejestrowanie fabryk obiektów kontrolnych w rejestrze systemu OLE.

Aby uzyskać więcej informacji na temat tworzenia obiektów, zobacz artykuły [Obiekty danych i źródła danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md) oraz Obiekty danych i źródła [danych: Tworzenie i niszczenie](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Aby uzyskać więcej informacji na temat rejestracji, zobacz artykuł [Rejestracja](../../mfc/registration.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="coleobjectfactorycoleobjectfactory"></a><a name="coleobjectfactory"></a>COleObjectFactory::COleObjectFactory

Konstruuje `COleObjectFactory` obiekt, inicjuje go jako fabrykę obiektów niezarejestrowanych i dodaje go do listy fabryk.

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

*Clsid*<br/>
Odwołanie do identyfikatora klasy OLE, który reprezentuje ta fabryka obiektów.

*pRuntimeClass (Klasa pRuntime)*<br/>
Wskaźnik do klasy czasu wykonywania obiektów C++ tej fabryki można utworzyć.

*bMultiInstance*<br/>
Wskazuje, czy pojedyncze wystąpienie aplikacji może obsługiwać wiele wystąpień. Jeśli TRUE, wiele wystąpień aplikacji są uruchamiane dla każdego żądania, aby utworzyć obiekt.

*nPłgi*<br/>
Zawiera co najmniej jedną z następujących flag:

- `afxRegDefault`Ustawia model gwintowania na ThreadingModel=Apartment.

- `afxRegInsertable`Umożliwia wyświetlenie formantu w oknie dialogowym **Wstawianie obiektu** dla obiektów OLE.

- `afxRegApartmentThreading`Ustawia model wątków w rejestrze na ThreadingModel=Apartment.

- `afxRegFreeThreading`Ustawia model wątków w rejestrze na ThreadingModel=Free.

   Można połączyć dwie `afxRegApartmentThreading` `afxRegFreeThreading` flagi i ustawić ThreadingModel=Both. Zobacz [InprocServer32](/windows/win32/com/inprocserver32) w windows SDK, aby uzyskać więcej informacji na temat rejestracji modelu wątkowości.

*lpszProgID*<br/>
Wskaźnik do ciągu zawierającego identyfikator programu słownego, taki jak "Microsoft Excel".

### <a name="remarks"></a>Uwagi

Aby użyć obiektu, należy go jednak zarejestrować.

Aby uzyskać więcej informacji, zobacz [ClsID klucz](/windows/win32/com/clsid-key-hklm) w windows SDK.

## <a name="coleobjectfactorygetclassid"></a><a name="getclassid"></a>COleObjectFactory::GetClassID

Zwraca odwołanie do identyfikatora klasy OLE, który reprezentuje ta fabryka.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do identyfikatora klasy OLE, który reprezentuje ta fabryka.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ClsID klucz](/windows/win32/com/clsid-key-hklm) w windows SDK.

## <a name="coleobjectfactorygetlicensekey"></a><a name="getlicensekey"></a>COleObjectFactory::GetLicenseKey

Żąda unikatowego klucza licencyjnego z biblioteki DLL formantu i przechowuje go w BSTR wskazanym przez *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwReserved (niesłuszne)*<br/>
Zarezerwowane do użytku w przyszłości.

*klawisz pbstrKey*<br/>
Wskaźnik do BSTR, który będzie przechowywać klucz licencyjny.

### <a name="return-value"></a>Wartość zwracana

Wartość niezerowa, jeśli ciąg klucza licencyjnego nie ma wartości NULL; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji zwraca wartość 0 i nie przechowuje niczego w BSTR. Jeśli używasz MFC ActiveX ControlWizard do utworzenia projektu, ControlWizard dostarcza zastąpienie, które pobiera klucz licencyjny formantu.

## <a name="coleobjectfactoryislicensevalid"></a><a name="islicensevalid"></a>COleObjectFactory::IsLicenseValid

Określa, czy licencja formantu jest ważna.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli successul; w przeciwnym razie fałszywe.

## <a name="coleobjectfactoryisregistered"></a><a name="isregistered"></a>COleObjectFactory::JestReregistered

Zwraca wartość niezerową, jeśli fabryka jest zarejestrowana w bibliotekach DLL systemu OLE.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli fabryka jest zarejestrowana; w przeciwnym razie 0.

## <a name="coleobjectfactoryoncreateobject"></a><a name="oncreateobject"></a>COleObjectFactory::OnCreateObject

Wywoływana przez strukturę, aby utworzyć nowy obiekt.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do utworzonego obiektu. Może zgłosić wyjątek pamięci, jeśli zakończy się niepowodzeniem.

### <a name="remarks"></a>Uwagi

Zastąpokaj tę funkcję, aby utworzyć obiekt z czegoś innego niż [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) przekazany do konstruktora.

## <a name="coleobjectfactoryregister"></a><a name="register"></a>COleObjectFactory::Zarejestruj się

Rejestruje tę fabrykę obiektów za pomocą bibliotek DLL systemu OLE.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli fabryka jest pomyślnie zarejestrowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana przez [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.

## <a name="coleobjectfactoryregisterall"></a><a name="registerall"></a>COleObjectFactory::RegisterAll

Rejestruje wszystkie fabryki obiektów aplikacji za pomocą bibliotek DLL systemu OLE.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli fabryki są pomyślnie zarejestrowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana przez [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.

## <a name="coleobjectfactoryrevoke"></a><a name="revoke"></a>COleObjectFactory::Odwołaj

Odwołuje rejestrację tej fabryki obiektów w bibliotekach DLL systemu OLE.

```
void Revoke();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję automatycznie przed zakończeniem aplikacji. W razie potrzeby wywołać go z zastąpienia [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

## <a name="coleobjectfactoryrevokeall"></a><a name="revokeall"></a>COleObjectFactory::RevokeAll

Odwołuje rejestracje wszystkich fabryk obiektów aplikacji za pomocą bibliotek DLL systemu OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Uwagi

Struktura wywołuje tę funkcję automatycznie przed zakończeniem aplikacji. W razie potrzeby wywołać go z zastąpienia [CWinApp::ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

## <a name="coleobjectfactoryunregisterall"></a><a name="unregisterall"></a>COleObjectFactory::WyrejestrowaćWszywszy

Wyrejestrowaj wszystkie fabryki obiektów aplikacji.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

## <a name="coleobjectfactoryupdateregistry"></a><a name="updateregistry"></a>COleObjectFactory::UpdateRegistry

Rejestruje wszystkie fabryki obiektów aplikacji w rejestrze systemu OLE.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parametry

*lpszProgID*<br/>
Wskaźnik do ciągu zawierającego identyfikator programu czytelny dla człowieka, taki jak "Excel.Document.5".

*Bregister*<br/>
Określa, czy fabryka obiektów klasy kontrolnej ma zostać zarejestrowana.

### <a name="remarks"></a>Uwagi

Krótkie dyskusje na temat dwóch form tej funkcji następują:

- **UpdateRegistry(** `lpszProgID` **)** Rejestruje tę fabrykę obiektów w rejestrze systemu OLE. Ta funkcja jest zwykle wywoływana przez [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.

- **UpdateRegistry(** `bRegister` **)** Ta forma funkcji jest nadpisywalna. Jeśli *bRegister* jest TRUE, ta funkcja rejestruje klasy kontroli z rejestru systemu. W przeciwnym razie wyrejestruje klasę.

   Jeśli używasz MFC ActiveX ControlWizard do utworzenia projektu, ControlWizard dostarcza zastąpienie tej czystej funkcji wirtualnej.

## <a name="coleobjectfactoryupdateregistryall"></a><a name="updateregistryall"></a>COleObjectFactory::UpdateRegistryAll

Rejestruje wszystkie fabryki obiektów aplikacji w rejestrze systemu OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*Bregister*<br/>
Określa, czy fabryka obiektów klasy kontrolnej ma zostać zarejestrowana.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli fabryki są pomyślnie zaktualizowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana przez [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) po uruchomieniu aplikacji.

## <a name="coleobjectfactoryverifylicensekey"></a><a name="verifylicensekey"></a>COleObjectFactory::VerifyLicenseKey

Sprawdza, czy kontener jest licencjonowany do używania formantu OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parametry

*klawisz bstrKey*<br/>
BSTR przechowywania wersji kontenera ciągu licencji.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli licencja w czasie wykonywania jest ważna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wersja domyślna wywołuje [GetLicenseKey,](#getlicensekey) aby uzyskać kopię ciągu licencji formantu i porównuje go z ciągiem w *bstrKey*. Jeśli dwa ciągi są zgodne, funkcja zwraca wartość niezerową; w przeciwnym razie zwraca 0.

Tę funkcję można zastąpić, aby zapewnić dostosowaną weryfikację licencji.

Funkcja [VerifyUserLicense](#verifyuserlicense) weryfikuje licencję w czasie projektowania.

## <a name="coleobjectfactoryverifyuserlicense"></a><a name="verifyuserlicense"></a>COleObjectFactory::VerifyUserLicense

Weryfikuje licencję czasu projektowania dla formantu OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli licencja na czas projektowania jest ważna; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
