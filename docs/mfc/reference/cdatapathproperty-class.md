---
title: Klasa CDataPathProperty
ms.date: 11/04/2016
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
ms.openlocfilehash: 89cb8ddcdd42643f52f755516e8845109163c57a
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780343"
---
# <a name="cdatapathproperty-class"></a>Klasa CDataPathProperty

Implementuje OLE kontrolować właściwość, która może być ładowana asynchronicznie.

## <a name="syntax"></a>Składnia

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Konstruuje `CDataPathProperty` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Name|Opis|
|----------|-----------------|
|[CDataPathProperty::GetControl](#getcontrol)|Pobiera asynchroniczny kontrolkę OLE skojarzone z `CDataPathProperty` obiektu.|
|[CDataPathProperty::GetPath](#getpath)|Pobiera nazwę właściwości ścieżki.|
|[CDataPathProperty::Open](#open)|Inicjuje Ładowanie asynchroniczne właściwości skojarzonego formantu ActiveX (OLE).|
|[CDataPathProperty::ResetData](#resetdata)|Wywołania `CAsyncMonikerFile::OnDataAvailable` powiadomić kontenera, w którym zostały zmienione właściwości formantu.|
|[CDataPathProperty::SetControl](#setcontrol)|Ustawia asynchronicznego skojarzony z właściwością kontrolki ActiveX (OLE).|
|[CDataPathProperty::SetPath](#setpath)|Ustawia nazwę właściwości ścieżki.|

## <a name="remarks"></a>Uwagi

Właściwości asynchronicznego są ładowane po rozpoczęciu synchroniczne.

Klasa `CDataPathProperty` jest tworzony na podstawie `CAysncMonikerFile`. Aby zaimplementować właściwości asynchronicznego w formantów OLE, należy wyprowadzić klasę z `CDataPathProperty`i zastępowania [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Aby uzyskać więcej informacji o sposobie używania formantów ActiveX i monikerów asynchronicznych w aplikacjach internetowych zobacz następujące artykuły:

- [Internet First Steps: ActiveX Controls](../../mfc/activex-controls-on-the-internet.md)

- [Internet First Steps: Monikery asynchroniczne](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

##  <a name="cdatapathproperty"></a>  CDataPathProperty::CDataPathProperty

Konstruuje `CDataPathProperty` obiektu.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Wskaźnik do obiektu sterowania OLE, który ma zostać skojarzony z tym `CDataPathProperty` obiektu.

*lpszPath*<br/>
Ścieżki, która może być bezwzględny lub względny, używane do tworzenia asynchronicznego moniker, odwołujący się do rzeczywistego lokalizacja bezwzględna właściwości. `CDataPathProperty` używa adresów URL, a nie nazwy plików. Jeśli chcesz `CDataPathProperty` obiektu dla pliku, dołączana `file://` do ścieżki.

### <a name="remarks"></a>Uwagi

`COleControl` Obiekt wskazywany przez *pControl* jest używany przez `Open` i pobrany przez klasy pochodne. Jeśli *pControl* ma wartość NULL, kontroli używane z `Open` powinna być ustawiona za pomocą `SetControl`. Jeśli *lpszPath* ma wartość NULL, można przekazać w ścieżce za pomocą `Open` lub ustaw go za pomocą `SetPath`.

##  <a name="getcontrol"></a>  CDataPathProperty::GetControl

Wywołaj tę funkcję elementu członkowskiego, aby pobrać `COleControl` obiekt skojarzony z `CDataPathProperty` obiektu.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do sterowania OLE skojarzone z `CDataPathProperty` obiektu. Wartość NULL, jeśli nie kontroli jest skojarzony.

##  <a name="getpath"></a>  CDataPathProperty::GetPath

Wywołaj tę funkcję elementu członkowskiego, aby pobrać ścieżki, ustaw, kiedy `CDataPathProperty` obiekt został skonstruowany, albo określony w `Open`, lub został określony w poprzednie wywołanie `SetPath` funkcja elementu członkowskiego.

```
CString GetPath() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę ścieżki do samej właściwości. Może być pusta, jeśli ścieżka nie została określona.

##  <a name="open"></a>  CDataPathProperty::Open

Wywołaj tę funkcję elementu członkowskiego, aby zainicjować ładowania właściwości asynchronicznego dla skojarzonego formantu.

```
virtual BOOL Open(
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    CFileException* pError = NULL);

virtual BOOL Open(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Wskaźnik do obiektu sterowania OLE, który ma zostać skojarzony z tym `CDataPathProperty` obiektu.

*pError*<br/>
Wskaźnik do wyjątku plików. W przypadku wystąpienia błędu zostanie ustawiona przyczynie.

*lpszPath*<br/>
Ścieżki, która może być bezwzględny lub względny, używane do tworzenia asynchronicznego moniker, odwołujący się do rzeczywistego lokalizacja bezwzględna właściwości. `CDataPathProperty` używa adresów URL, a nie nazwy plików. Jeśli chcesz `CDataPathProperty` obiektu dla pliku, dołączana `file://` do ścieżki.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja próbuje uzyskać `IBindHost` interfejsu z formantu.

Przed wywołaniem `Open` bez ścieżki, należy ustawić wartość dla właściwości ścieżki. Można to zrobić, gdy obiekt jest zbudowany, lub przez wywołanie `SetPath` funkcja elementu członkowskiego.

Przed wywołaniem `Open` bez kontroli kontrolki ActiveX (dawniej kontrolka OLE) może być skojarzony z obiektem. Można to zrobić, gdy obiekt jest zbudowany, lub przez wywołanie `SetControl`.

Wszystkie przeciążenia [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) są także dostępne z `CDataPathProperty`.

##  <a name="resetdata"></a>  CDataPathProperty::ResetData

Wywołaj tę funkcję, aby uzyskać `CAsyncMonikerFile::OnDataAvailable` powiadomić kontenera, że właściwości kontrolki uległy zmianie, a wszystkie informacje, które są ładowane asynchronicznie nie jest już przydatna.

```
virtual void ResetData();
```

### <a name="remarks"></a>Uwagi

Otwieranie powinny zostać ponownie uruchomione. Klasy pochodne mogą zastąpić tę funkcję dla różnych ustawień domyślnych.

##  <a name="setcontrol"></a>  CDataPathProperty::SetControl

Wywołaj tę funkcję elementu członkowskiego, aby skojarzyć asynchronicznego kontrolkę OLE z `CDataPathProperty` obiektu.

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Parametry

*pControl*<br/>
Wskaźnik do asynchronicznego kontrolkę OLE ma zostać skojarzony z właściwością.

##  <a name="setpath"></a>  CDataPathProperty::SetPath

Wywołaj tę funkcję elementu członkowskiego, aby ustawić nazwę ścieżki właściwości.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Parametry

*lpszPath*<br/>
Ścieżką, która może być bezwzględny lub względny, do właściwości są ładowane asynchronicznie. `CDataPathProperty` używa adresów URL, a nie nazwy plików. Jeśli chcesz `CDataPathProperty` obiektu dla pliku, dołączana `file://` do ścieżki.

## <a name="see-also"></a>Zobacz także

[Obraz przykładowej MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
