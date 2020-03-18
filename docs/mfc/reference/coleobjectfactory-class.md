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
ms.openlocfilehash: 22805550d13ecb400b151495363e5eda2dfb3b76
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421542"
---
# <a name="coleobjectfactory-class"></a>Klasa COleObjectFactory

Implementuje fabrykę klas OLE, która tworzy obiekty OLE, takie jak serwery, obiekty automatyzacji i dokumenty.

## <a name="syntax"></a>Składnia

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleObjectFactory:: COleObjectFactory](#coleobjectfactory)|Konstruuje obiekt `COleObjectFactory`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleObjectFactory:: GetClassID](#getclassid)|Zwraca identyfikator klasy OLE obiektów tworzonych przez tę fabrykę.|
|[COleObjectFactory:: IsLicenseValid](#islicensevalid)|Określa, czy licencja kontrolki jest prawidłowa.|
|[COleObjectFactory:: IsRegistered](#isregistered)|Wskazuje, czy fabryka obiektów jest zarejestrowana w bibliotekach DLL systemu OLE.|
|[COleObjectFactory:: register](#register)|Rejestruje fabrykę obiektów przy użyciu bibliotek DLL systemu OLE.|
|[COleObjectFactory:: RegisterAll](#registerall)|Rejestruje wszystkie fabryki obiektów aplikacji za pomocą bibliotek DLL systemu OLE.|
|[COleObjectFactory:: odwołaj](#revoke)|Odwołuje rejestrację fabryki obiektów przy użyciu bibliotek DLL systemu OLE.|
|[COleObjectFactory:: RevokeAll](#revokeall)|Odwoływanie rejestracji fabryk obiektów aplikacji za pomocą bibliotek DLL systemu OLE.|
|[COleObjectFactory:: UnregisterAll](#unregisterall)|Wyrejestrowuje wszystkie fabryki obiektów aplikacji.|
|[COleObjectFactory:: operacja UpdateRegistry](#updateregistry)|Rejestruje fabrykę obiektów przy użyciu rejestru systemu OLE.|
|[COleObjectFactory:: UpdateRegistryAll](#updateregistryall)|Rejestruje wszystkie fabryki obiektów aplikacji z rejestrem systemu OLE.|

### <a name="protected-methods"></a>Metody chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[COleObjectFactory:: GetLicenseKey](#getlicensekey)|Żąda unikatowego klucza z biblioteki DLL kontrolki.|
|[COleObjectFactory:: oncreateobject](#oncreateobject)|Wywoływane przez platformę, aby utworzyć nowy obiekt typu fabryki.|
|[COleObjectFactory:: VerifyLicenseKey](#verifylicensekey)|Sprawdza, czy klucz osadzony w formancie jest zgodny z kluczem osadzonym w kontenerze.|
|[COleObjectFactory:: VerifyUserLicense](#verifyuserlicense)|Sprawdza, czy formant jest licencjonowany do użycia w czasie projektowania.|

## <a name="remarks"></a>Uwagi

Klasa `COleObjectFactory` ma funkcje członkowskie do wykonywania następujących funkcji:

- Zarządzanie rejestracją obiektów.

- Aktualizacja rejestru systemu OLE, a także Rejestracja w czasie wykonywania, która informuje OLE, że obiekty są uruchomione i gotowe do odbierania komunikatów.

- Wymuszanie licencjonowania przez ograniczenie użycia kontroli do licencjonowanych deweloperów w czasie projektowania i Licencjonowanie aplikacji w czasie wykonywania.

- Rejestrowanie fabryk obiektów kontroli przy użyciu rejestru systemu OLE.

Aby uzyskać więcej informacji na temat tworzenia obiektów, zobacz artykuł [obiekty danych i źródła danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md) oraz [obiekty danych i źródła danych: Tworzenie i niszczenie](../../mfc/data-objects-and-data-sources-creation-and-destruction.md). Aby uzyskać więcej informacji na temat rejestracji, zobacz [rejestracja](../../mfc/registration.md)artykułu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

##  <a name="coleobjectfactory"></a>COleObjectFactory:: COleObjectFactory

Konstruuje obiekt `COleObjectFactory`, inicjuje go jako niezarejestrowaną fabrykę obiektów i dodaje go do listy fabryk.

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

*Identyfikator*<br/>
Odwołanie do identyfikatora klasy OLE reprezentowanego przez fabrykę obiektów.

*pRuntimeClass*<br/>
Wskaźnik do klasy czasu wykonywania obiektów tworzonych przez C++ tę fabrykę.

*bMultiInstance*<br/>
Wskazuje, czy pojedyncze wystąpienie aplikacji może obsługiwać wiele wystąpień. W przypadku wartości TRUE dla każdego żądania utworzenia obiektu uruchamiane jest wiele wystąpień aplikacji.

*nFlags*<br/>
Zawiera co najmniej jedną z następujących flag:

- `afxRegDefault` ustawia model wątkowości na ThreadingModel = Apartment.

- `afxRegInsertable` umożliwia wyświetlenie formantu w oknie dialogowym **Wstaw obiekt** dla obiektów OLE.

- `afxRegApartmentThreading` ustawia model wątkowości w rejestrze na ThreadingModel = Apartment.

- `afxRegFreeThreading` ustawia model wątkowości w rejestrze, aby ThreadingModel = Free.

   Można połączyć dwie flagi `afxRegApartmentThreading` i `afxRegFreeThreading`, aby ustawić ThreadingModel = oba. Aby uzyskać więcej informacji na temat rejestracji modelu wątków, zobacz [InprocServer32](/windows/win32/com/inprocserver32) w Windows SDK.

*lpszProgID*<br/>
Wskaźnik do ciągu zawierającego werbalny identyfikator programu, taki jak "Microsoft Excel".

### <a name="remarks"></a>Uwagi

Aby użyć obiektu, należy jednak go zarejestrować.

Aby uzyskać więcej informacji, zobacz [klucz CLSID](/windows/win32/com/clsid-key-hklm) w Windows SDK.

##  <a name="getclassid"></a>COleObjectFactory:: GetClassID

Zwraca odwołanie do identyfikatora klasy OLE reprezentowanego przez fabrykę.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do identyfikatora klasy OLE reprezentowanego przez tę fabrykę.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [klucz CLSID](/windows/win32/com/clsid-key-hklm) w Windows SDK.

##  <a name="getlicensekey"></a>COleObjectFactory:: GetLicenseKey

Żąda unikatowego klucza licencji z biblioteki DLL kontrolki i zapisuje ją w postaci BSTR wskazanej przez *pbstrKey*.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>Parametry

*dwReserved*<br/>
Zarezerwowany do użytku w przyszłości.

*pbstrKey*<br/>
Wskaźnik na BSTR, który będzie przechowywać klucz licencji.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli ciąg klucza licencji nie ma wartości NULL; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna implementacja tej funkcji zwraca 0 i nie przechowuje niczego w elemencie BSTR. Jeśli do utworzenia projektu używasz programu MFC ActiveX ControlWizard, ControlWizard dostarcza przesłonięcie, które Pobiera klucz licencji formantu.

##  <a name="islicensevalid"></a>COleObjectFactory:: IsLicenseValid

Określa, czy licencja kontrolki jest prawidłowa.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>Wartość zwrócona

PRAWDA, jeśli successul; w przeciwnym razie false.

##  <a name="isregistered"></a>COleObjectFactory:: IsRegistered

Zwraca wartość różną od zera, jeśli fabryka jest zarejestrowana w bibliotekach DLL systemu OLE.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli fabryka jest zarejestrowana; w przeciwnym razie 0.

##  <a name="oncreateobject"></a>COleObjectFactory:: oncreateobject

Wywoływane przez platformę, by utworzyć nowy obiekt.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do utworzonego obiektu. Może zgłosić wyjątek pamięci, jeśli nie powiedzie się.

### <a name="remarks"></a>Uwagi

Przesłoń tę funkcję, aby utworzyć obiekt z elementu innego niż [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) do konstruktora.

##  <a name="register"></a>COleObjectFactory:: register

Rejestruje fabrykę obiektów przy użyciu bibliotek DLL systemu OLE.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli fabryka została pomyślnie zarejestrowana; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana przez [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) , gdy aplikacja jest uruchamiana.

##  <a name="registerall"></a>COleObjectFactory:: RegisterAll

Rejestruje wszystkie fabryki obiektów aplikacji za pomocą bibliotek DLL systemu OLE.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli fabryki zostały pomyślnie zarejestrowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana przez [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) , gdy aplikacja jest uruchamiana.

##  <a name="revoke"></a>COleObjectFactory:: odwołaj

Odwołuje rejestrację fabryki obiektów przy użyciu bibliotek DLL systemu OLE.

```
void Revoke();
```

### <a name="remarks"></a>Uwagi

Struktura automatycznie wywołuje tę funkcję przed zakończeniem działania aplikacji. W razie potrzeby Wywołaj ją z zastąpienia elementu [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="revokeall"></a>COleObjectFactory:: RevokeAll

Odwołuje wszystkie rejestracje fabryk obiektów aplikacji za pomocą bibliotek DLL systemu OLE.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>Uwagi

Struktura automatycznie wywołuje tę funkcję przed zakończeniem działania aplikacji. W razie potrzeby Wywołaj ją z zastąpienia elementu [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance).

##  <a name="unregisterall"></a>COleObjectFactory:: UnregisterAll

Wyrejestrowuje wszystkie fabryki obiektów aplikacji.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

##  <a name="updateregistry"></a>COleObjectFactory:: operacja UpdateRegistry

Rejestruje wszystkie fabryki obiektów aplikacji z rejestrem systemu OLE.

```
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>Parametry

*lpszProgID*<br/>
Wskaźnik na ciąg zawierający identyfikator programu czytelny dla człowieka, taki jak "Excel. Document. 5".

*bRegister*<br/>
Określa, czy fabryka obiektów klasy kontrolki ma zostać zarejestrowana.

### <a name="remarks"></a>Uwagi

Krótkie dyskusje na temat dwóch formularzy dla tej funkcji są następujące:

- **Operacja UpdateRegistry (** `lpszProgID` **)** Rejestruje fabrykę obiektów przy użyciu rejestru systemu OLE. Ta funkcja jest zwykle wywoływana przez [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) , gdy aplikacja jest uruchamiana.

- **Operacja UpdateRegistry (** `bRegister` **)** Ta forma funkcji jest możliwy do zastąpienia. Jeśli *bRegister* ma wartość true, ta funkcja rejestruje klasę formantów z rejestrem systemowym. W przeciwnym razie wyrejestruje klasę.

   Jeśli do utworzenia projektu używasz programu MFC ActiveX ControlWizard, ControlWizard dostarcza przesłonięcie tej czystej funkcji wirtualnej.

##  <a name="updateregistryall"></a>COleObjectFactory:: UpdateRegistryAll

Rejestruje wszystkie fabryki obiektów aplikacji z rejestrem systemu OLE.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*bRegister*<br/>
Określa, czy fabryka obiektów klasy kontrolki ma zostać zarejestrowana.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli fabryki zostały pomyślnie zaktualizowane; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana przez [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) , gdy aplikacja jest uruchamiana.

##  <a name="verifylicensekey"></a>COleObjectFactory:: VerifyLicenseKey

Sprawdza, czy kontener ma licencję na korzystanie z kontrolki OLE.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>Parametry

*bstrKey*<br/>
BSTR — przechowywanie wersji ciągu licencji.

### <a name="return-value"></a>Wartość zwrócona

Różne od zera, jeśli licencja czasu wykonywania jest prawidłowa; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Domyślna wersja wywołuje [GetLicenseKey](#getlicensekey) , aby uzyskać kopię ciągu licencji kontrolki i porównuje ją z ciągiem w *bstrKey*. Jeśli dwa ciągi są zgodne, funkcja zwraca wartość różną od zera. w przeciwnym razie zwraca wartość 0.

Można zastąpić tę funkcję, aby zapewnić dostosowaną weryfikację licencji.

Funkcja [VerifyUserLicense](#verifyuserlicense) weryfikuje licencję czasu projektowania.

##  <a name="verifyuserlicense"></a>COleObjectFactory:: VerifyUserLicense

Weryfikuje licencję czasu projektowania dla kontrolki OLE.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>Wartość zwrócona

Niezerowe, jeśli licencja czasu projektowania jest prawidłowa; w przeciwnym razie 0.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)
