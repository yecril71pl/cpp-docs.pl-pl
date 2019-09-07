---
title: Klasa COleDataObject
ms.date: 11/04/2016
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
ms.openlocfilehash: e706489a84ad564949e2c2d3d193173fc19b9828
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741626"
---
# <a name="coledataobject-class"></a>Klasa COleDataObject

Używany w transferach danych do pobierania danych w różnych formatach ze schowka poprzez przeciąganie i upuszczanie lub z osadzonego elementu OLE.

## <a name="syntax"></a>Składnia

```
class COleDataObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|Konstruuje `COleDataObject` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDataObject:: Attach](#attach)|Dołącza określony obiekt danych OLE do `COleDataObject`.|
|[COleDataObject::AttachClipboard](#attachclipboard)|Dołącza obiekt danych znajdujący się w Schowku.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Przygotowuje się do jednego lub `GetNextFormat` większej liczby kolejnych wywołań.|
|[COleDataObject::Detach](#detach)|Odłącza skojarzony `IDataObject` obiekt.|
|[COleDataObject:: GetData](#getdata)|Kopiuje dane z dołączonego obiektu danych OLE w określonym formacie.|
|[COleDataObject::GetFileData](#getfiledata)|Kopiuje dane z dołączonego obiektu OLE Data do `CFile` wskaźnika w określonym formacie.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Kopiuje dane z dołączonego obiektu danych OLE do `HGLOBAL` w określonym formacie.|
|[COleDataObject::GetNextFormat](#getnextformat)|Zwraca następny dostępny format danych.|
|[COleDataObject::IsDataAvailable](#isdataavailable)|Sprawdza, czy dane są dostępne w określonym formacie.|
|[COleDataObject:: Release](#release)|Odłącza i zwalnia skojarzony `IDataObject` obiekt.|

## <a name="remarks"></a>Uwagi

`COleDataObject`nie ma klasy bazowej.

Te rodzaje transferów danych obejmują źródło i miejsce docelowe. Źródło danych jest implementowane jako obiekt klasy [by uzyskać COleDataSource](../../mfc/reference/coledatasource-class.md) . Za każdym razem, gdy w aplikacji docelowej znajdują się w niej dane lub jest wyświetlany monit o wykonanie operacji wklejenia ze schowka, `COleDataObject` należy utworzyć obiekt klasy.

Ta klasa umożliwia określenie, czy dane istnieją w określonym formacie. Możesz również wyliczyć dostępne formaty danych lub sprawdzić, czy dany format jest dostępny, a następnie pobrać dane w preferowanym formacie. Pobieranie obiektów można wykonać na kilka różnych sposobów, w tym użycie [CFile](../../mfc/reference/cfile-class.md), HGLOBAL lub `STGMEDIUM` struktury.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w Windows SDK.

Aby uzyskać więcej informacji na temat używania obiektów danych w aplikacji, zobacz temat [obiekty danych artykułu i źródła danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`COleDataObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="attach"></a>COleDataObject:: Attach

Wywołaj tę funkcję, aby `COleDataObject` skojarzyć obiekt z obiektem danych OLE.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDataObject*<br/>
Wskazuje obiekt danych OLE.

*bAutoRelease*<br/>
Ma wartość true, jeśli obiekt danych OLE ma zostać wydzierżawiony, gdy `COleDataObject` obiekt jest niszczony; w przeciwnym razie false.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) w Windows SDK.

##  <a name="attachclipboard"></a>COleDataObject::AttachClipboard

Wywołaj tę funkcję, aby dołączyć obiekt danych, który znajduje się obecnie w schowku do `COleDataObject` obiektu.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Wywołanie tej funkcji powoduje zablokowanie schowka do momentu zwolnienia tego obiektu danych. Obiekt danych jest wydawany w destruktorze dla `COleDataObject`. Aby uzyskać więcej informacji, zobacz [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) i [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) w dokumencie Win32.

##  <a name="beginenumformats"></a>COleDataObject::BeginEnumFormats

Wywołaj tę funkcję, aby przygotować się do `GetNextFormat` kolejnych wywołań do pobierania listy formatów danych z elementu.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `BeginEnumFormats`, pozycja pierwszego formatu obsługiwanego przez ten obiekt danych jest przechowywana. Kolejne wywołania do `GetNextFormat` programu wyliczają listę dostępnych formatów w obiekcie danych.

Aby sprawdzić dostępność danych w danym formacie, użyj [COleDataObject:: IsDataAvailable](#isdataavailable).

Aby uzyskać więcej informacji, zobacz [IDataObject:: EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) w Windows SDK.

##  <a name="coledataobject"></a>COleDataObject::COleDataObject

Konstruuje `COleDataObject` obiekt.

```
COleDataObject();
```

### <a name="remarks"></a>Uwagi

Wywołanie [COleDataObject:: Attach](#attach) lub [COleDataObject:: AttachClipboard](#attachclipboard) musi zostać wykonane przed wywołaniem innych `COleDataObject` funkcji.

> [!NOTE]
>  Ponieważ jeden z parametrów obsługi przeciągania i upuszczania jest wskaźnikiem do `COleDataObject`, nie ma potrzeby wywoływania tego konstruktora w celu obsługi przeciągania i upuszczania.

##  <a name="detach"></a>COleDataObject::D etach

Wywołaj tę funkcję, aby `COleDataObject` odłączyć obiekt od skojarzonego obiektu danych OLE bez zwalniania obiektu danych.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu danych OLE, który został odłączony.

### <a name="remarks"></a>Uwagi

##  <a name="getdata"></a>COleDataObject:: GetData

Wywołaj tę funkcję, aby pobrać dane z elementu w określonym formacie.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format, w którym dane mają zostać zwrócone. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwracaną przez natywną funkcję [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) systemu Windows.

*lpStgMedium*<br/>
Wskazuje na strukturę [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) , która będzie odbierać dane.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym dane mają być zwracane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie spoza formatu Schowka określonego przez *cfFormat*. Jeśli wartość jest równa null, wartości domyślne są używane dla innych pól `FORMATETC` struktury.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w Windows SDK.

##  <a name="getfiledata"></a>COleDataObject::GetFileData

Wywołaj tę funkcję, aby `CFile` utworzyć `CFile`obiekt pochodny i pobrać dane w określonym formacie `CFile` do wskaźnika.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format, w którym dane mają zostać zwrócone. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwracaną przez natywną funkcję [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) systemu Windows.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym dane mają być zwracane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie spoza formatu Schowka określonego przez *cfFormat*. Jeśli wartość jest równa null, wartości domyślne są używane dla innych pól `FORMATETC` struktury.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego `CFile` lub `CFile`pochodnego obiektu zawierającego dane, jeśli to się powiedzie; w przeciwnym razie wartość null.

### <a name="remarks"></a>Uwagi

W zależności od średniej dane są przechowywane w, faktyczny typ wskazywany przez wartość zwracaną może być `CFile`, `CSharedFile`lub `COleStreamFile`.

> [!NOTE]
>  `CFile` Obiekt, do którego uzyskuje dostęp wartość zwracana przez tę funkcję, należy do obiektu wywołującego. `CFile` Obiekt wywołujący jest odpowiedzialny za **usunięcie** obiektu, w związku z czym zamyka plik.

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w Windows SDK.

##  <a name="getglobaldata"></a>COleDataObject::GetGlobalData

Wywołaj tę funkcję, aby przydzielić blok pamięci globalnej i pobrać dane w określonym formacie do HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format, w którym dane mają zostać zwrócone. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwracaną przez natywną funkcję [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) systemu Windows.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym dane mają być zwracane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie spoza formatu Schowka określonego przez *cfFormat*. Jeśli wartość jest równa null, wartości domyślne są używane dla innych pól `FORMATETC` struktury.

### <a name="return-value"></a>Wartość zwracana

Dojście bloku pamięci globalnej zawierające dane, jeśli się to powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w Windows SDK.

##  <a name="getnextformat"></a>COleDataObject::GetNextFormat

Wywołaj tę funkcję wielokrotnie, aby uzyskać wszystkie formaty dostępne do pobierania danych z elementu.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , która otrzymuje informacje o formacie, gdy wywołanie funkcji zwraca.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli jest dostępny inny format; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po wywołaniu [COleDataObject:: BeginEnumFormats](#beginenumformats)pozycja pierwszego formatu obsługiwanego przez ten obiekt danych jest przechowywana. Kolejne wywołania do `GetNextFormat` programu wyliczają listę dostępnych formatów w obiekcie danych. Użyj tych funkcji, aby wyświetlić listę dostępnych formatów.

Aby sprawdzić dostępność danego formatu, wywołaj [COleDataObject:: IsDataAvailable](#isdataavailable).

Aby uzyskać więcej informacji, zobacz [IEnumXXXX:: Next](/previous-versions//ms695273\(v=vs.85\)) w Windows SDK.

##  <a name="isdataavailable"></a>COleDataObject::IsDataAvailable

Wywołaj tę funkcję, aby określić, czy konkretny format jest dostępny do pobierania danych z elementu OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format danych schowka, który ma być używany w strukturze wskazywanym przez *lpFormatEtc*. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwracaną przez natywną funkcję [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) systemu Windows.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą żądany format. Podaj wartość dla tego parametru tylko wtedy, gdy chcesz określić dodatkowe informacje o formacie spoza formatu Schowka określonego przez *cfFormat*. Jeśli wartość jest równa null, wartości domyślne są używane dla innych pól `FORMATETC` struktury.

### <a name="return-value"></a>Wartość zwracana

Wartość różna od zera, jeśli dane są dostępne w określonym formacie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna przed `GetData`wywołaniem `GetFileData`,, `GetGlobalData`lub.

Aby uzyskać więcej informacji, zobacz [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CRichEditView:: QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

##  <a name="release"></a>COleDataObject:: Release

Wywołaj tę funkcję, aby zwolnić własność obiektu [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) , który został wcześniej skojarzony z `COleDataObject` obiektem.

```
void Release();
```

### <a name="remarks"></a>Uwagi

Zostało skojarzone `Attach` z przez wywołanie metody lub `AttachClipboard` bezpośrednio lub przez platformę. `COleDataObject` `IDataObject` Jeśli `Attach` parametr *bAutoRelease* `IDataObject` ma wartość false, obiekt nie zostanie wypublikowany. W takim przypadku obiekt wywołujący jest odpowiedzialny za zwolnienie `IDataObject` przez wywołanie [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Zobacz także

[Przykład HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład OCLIENT MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDataSource](../../mfc/reference/coledatasource-class.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)
