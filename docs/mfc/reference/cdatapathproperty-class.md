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
ms.openlocfilehash: e96106dcd6f496c6cc99c9d72d86052547b6d06b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376468"
---
# <a name="cdatapathproperty-class"></a>Klasa CDataPathProperty

Implementuje właściwość formantu OLE, która może być ładowana asynchronicznie.

## <a name="syntax"></a>Składnia

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Właściwości CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Konstruuje `CDataPathProperty` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Właściwości CDataPathProperty::GetControl](#getcontrol)|Pobiera asynchroniiowy formant OLE `CDataPathProperty` skojarzony z obiektem.|
|[Właściwości CDataPathProperty::GetPath](#getpath)|Pobiera nazwa ścieżki właściwości.|
|[CDataPathProperty::Otwórz](#open)|Inicjuje ładowanie właściwości asynchronii dla skojarzonego formantu ActiveX (OLE).|
|[Właściwości CDataPathProperty::ResetData](#resetdata)|Wywołania `CAsyncMonikerFile::OnDataAvailable` powiadamiania kontenera, że właściwości formantu zostały zmienione.|
|[CDataPathProperty::SetControl](#setcontrol)|Ustawia asynchroniiowy ActiveX (OLE) kontroli skojarzonej z właściwością.|
|[CDataPathProperty::SetPath](#setpath)|Ustawia nazwa ścieżki właściwości.|

## <a name="remarks"></a>Uwagi

Właściwości asynchroniczne są ładowane po zainicjowaniu synchronicznym.

Klasa `CDataPathProperty` jest pochodną `CAysncMonikerFile`. Aby zaimplementować właściwości asynchroniczne w formantyku OLE, należy wyprowadzić klasę z `CDataPathProperty`, i zastąpić [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).

Aby uzyskać więcej informacji na temat używania monikerów asynchronicznych i formantów ActiveX w aplikacjach internetowych, zobacz następujące artykuły:

- [Pierwsze kroki w Internecie: Formanty ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Pierwsze kroki internetowe: Asynchroniczne Monikers](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

[Colestreamfile](../../mfc/reference/colestreamfile-class.md)

[Plik CMoniker](../../mfc/reference/cmonikerfile-class.md)

[Casyncmonikerfile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="cdatapathpropertycdatapathproperty"></a><a name="cdatapathproperty"></a>Właściwości CDataPathProperty::CDataPathProperty

Konstruuje `CDataPathProperty` obiekt.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parametry

*pKontroluj*<br/>
Wskaźnik do obiektu sterującego OLE, który `CDataPathProperty` ma być skojarzony z tym obiektem.

*lpszPath (lpszPath)*<br/>
Ścieżka, która może być bezwzględna lub względna, używana do tworzenia asynchroniiowego monikera, który odwołuje się do rzeczywistej bezwzględnej lokalizacji właściwości. `CDataPathProperty`używa adresów URL, a nie nazwy plików. Jeśli chcesz `CDataPathProperty` obiekt dla pliku, `file://` należy dołączyć do ścieżki.

### <a name="remarks"></a>Uwagi

Obiekt `COleControl` wskazany przez *pControl* `Open` jest używany przez i pobierane przez klasy pochodne. Jeśli *pControl* ma wartość NULL, formant używany z `Open` należy ustawić za pomocą `SetControl`. Jeśli *lpszPath* ma wartość NULL, można `Open` przejść ścieżką lub ustawić ją za pomocą `SetPath`.

## <a name="cdatapathpropertygetcontrol"></a><a name="getcontrol"></a>Właściwości CDataPathProperty::GetControl

Wywołanie tej funkcji elementu `COleControl` członkowskiego, aby `CDataPathProperty` pobrać obiekt skojarzony z obiektem.

```
COleControl* GetControl();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do formantu OLE `CDataPathProperty` skojarzonego z obiektem. Null, jeśli nie formant jest skojarzony.

## <a name="cdatapathpropertygetpath"></a><a name="getpath"></a>Właściwości CDataPathProperty::GetPath

Wywołanie tej funkcji elementu członkowskiego, aby `CDataPathProperty` pobrać ścieżkę, ustawić, kiedy obiekt został skonstruowany lub określony w `Open`, lub określone w poprzednim wywołaniu funkcji `SetPath` elementu członkowskiego.

```
CString GetPath() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca nazwę ścieżki do samej właściwości. Może być pusta, jeśli nie określono żadnej ścieżki.

## <a name="cdatapathpropertyopen"></a><a name="open"></a>CDataPathProperty::Otwórz

Wywołanie tej funkcji elementu członkowskiego, aby zainicjować ładowanie właściwości asynchronii dla skojarzonego formantu.

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

*pKontroluj*<br/>
Wskaźnik do obiektu sterującego OLE, który `CDataPathProperty` ma być skojarzony z tym obiektem.

*Perror*<br/>
Wskaźnik do wyjątku pliku. W przypadku wystąpienia błędu zostanie ustawiona na przyczynę.

*lpszPath (lpszPath)*<br/>
Ścieżka, która może być bezwzględna lub względna, używana do tworzenia asynchroniiowego monikera, który odwołuje się do rzeczywistej bezwzględnej lokalizacji właściwości. `CDataPathProperty`używa adresów URL, a nie nazwy plików. Jeśli chcesz `CDataPathProperty` obiekt dla pliku, `file://` należy dołączyć do ścieżki.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja próbuje uzyskać `IBindHost` interfejs z formantu.

Przed `Open` wywołaniem bez ścieżki należy ustawić wartość ścieżki właściwości. Można to zrobić, gdy obiekt jest konstruowany lub wywołując funkcję `SetPath` elementu członkowskiego.

Przed `Open` wywołaniem bez kontroli formant ActiveX (dawniej znany jako formant OLE) może być skojarzony z obiektem. Można to zrobić, gdy obiekt jest konstruowany lub wywołując `SetControl`.

Wszystkie przeciążenia [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) są `CDataPathProperty`również dostępne od .

## <a name="cdatapathpropertyresetdata"></a><a name="resetdata"></a>Właściwości CDataPathProperty::ResetData

Wywołanie tej `CAsyncMonikerFile::OnDataAvailable` funkcji, aby powiadomić kontener, że właściwości formantu zostały zmienione, a wszystkie informacje ładowane asynchronicznie nie jest już przydatne.

```
virtual void ResetData();
```

### <a name="remarks"></a>Uwagi

Otwarcie powinno zostać ponownie uruchomione. Klasy pochodne mogą zastąpić tę funkcję dla różnych wartości domyślnych.

## <a name="cdatapathpropertysetcontrol"></a><a name="setcontrol"></a>CDataPathProperty::SetControl

Wywołanie tej funkcji elementu członkowskiego, aby skojarzyć asynchronisty formant OLE z obiektem. `CDataPathProperty`

```
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>Parametry

*pKontroluj*<br/>
Wskaźnik do asynchroniiowego formantu OLE, który ma być skojarzony z właściwością.

## <a name="cdatapathpropertysetpath"></a><a name="setpath"></a>CDataPathProperty::SetPath

Wywołanie tej funkcji elementu członkowskiego, aby ustawić nazwa ścieżki właściwości.

```
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>Parametry

*lpszPath (lpszPath)*<br/>
Ścieżka, która może być bezwzględna lub względna, do właściwości ładowanej asynchronicznie. `CDataPathProperty`używa adresów URL, a nie nazwy plików. Jeśli chcesz `CDataPathProperty` obiekt dla pliku, `file://` należy dołączyć do ścieżki.

## <a name="see-also"></a>Zobacz też

[Przykładowy obraz MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
