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
ms.openlocfilehash: 5e1545a033ab482e838fbc944b0ca9b3e543d651
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366128"
---
# <a name="coledataobject-class"></a>Klasa COleDataObject

Używane w transferach danych do pobierania danych w różnych formatach ze Schowka, przez przeciąganie i upuszczanie lub z osadzonego elementu OLE.

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
|[COleDataObject::Dołącz](#attach)|Dołącza określony obiekt danych OLE `COleDataObject`do pliku .|
|[COleDataObject::AttachClipboard](#attachclipboard)|Dołącza obiekt danych, który znajduje się w Schowku.|
|[COleDataObject::BeginEnumFormaty](#beginenumformats)|Przygotowuje się do jednego `GetNextFormat` lub więcej kolejnych połączeń.|
|[COleDataObject::Detach](#detach)|Odłącza skojarzony `IDataObject` obiekt.|
|[COleDataObject::GetData](#getdata)|Kopiuje dane z dołączonego obiektu danych OLE w określonym formacie.|
|[COleDataObject::GetFileData](#getfiledata)|Kopiuje dane z dołączonego obiektu `CFile` danych OLE do wskaźnika w określonym formacie.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Kopiuje dane z dołączonego obiektu `HGLOBAL` danych OLE do określonego formatu.|
|[COleDataObject::GetNextFormat](#getnextformat)|Zwraca następny dostępny format danych.|
|[COleDataObject::IsDataDostępne](#isdataavailable)|Sprawdza, czy dane są dostępne w określonym formacie.|
|[COleDataObject::Release COleDataObject::Release COleDataObject::Release COle](#release)|Odłącza i zwalnia `IDataObject` skojarzony obiekt.|

## <a name="remarks"></a>Uwagi

`COleDataObject`nie ma klasy podstawowej.

Tego rodzaju transfery danych obejmują źródło i miejsce docelowe. Źródło danych jest implementowane jako obiekt [COleDataSource](../../mfc/reference/coledatasource-class.md) klasy. Za każdym razem, gdy aplikacja docelowa ma dane porzucone w nim lub jest `COleDataObject` proszony o wykonanie operacji wklejania ze Schowka, należy utworzyć obiekt klasy.

Ta klasa umożliwia określenie, czy dane istnieją w określonym formacie. Można również wyliczyć dostępne formaty danych lub sprawdzić, czy dany format jest dostępny, a następnie pobrać dane w preferowanym formacie. Pobieranie obiektów można wykonać na kilka różnych sposobów, w tym przy użyciu [CFile](../../mfc/reference/cfile-class.md), HGLOBAL lub `STGMEDIUM` struktury.

Aby uzyskać więcej informacji, zobacz strukturę [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w sdk systemu Windows.

Aby uzyskać więcej informacji na temat używania obiektów danych w aplikacji, zobacz artykuł [Obiekty danych i źródła danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`COleDataObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleDataObject::Dołącz

Wywołanie tej funkcji, aby skojarzyć `COleDataObject` obiekt z obiektem danych OLE.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDataObject*<br/>
Wskazuje obiekt danych OLE.

*bAutoRelease*<br/>
PRAWDA, jeśli obiekt danych OLE `COleDataObject` powinien zostać zwolniony, gdy obiekt zostanie zniszczony; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) w windows SDK.

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject::AttachClipboard

Wywołanie tej funkcji, aby dołączyć obiekt danych, który `COleDataObject` znajduje się obecnie w Schowku do obiektu.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Wywołanie tej funkcji blokuje Schowek, dopóki ten obiekt danych nie zostanie zwolniony. Obiekt danych jest zwalniany w destruktorze `COleDataObject`dla pliku . Aby uzyskać więcej informacji, zobacz [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) i [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) w dokumencie Win32.

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject::BeginEnumFormaty

Wywołanie tej funkcji, aby `GetNextFormat` przygotować się do kolejnych wywołań do pobierania listy formatów danych z elementu.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `BeginEnumFormats`, pozycja pierwszego formatu obsługiwanego przez ten obiekt danych jest przechowywana. Kolejne wywołania `GetNextFormat` wyliczą listę dostępnych formatów w obiekcie danych.

Aby sprawdzić dostępność danych w danym formacie, należy użyć [COleDataObject::IsDataAvailable](#isdataavailable).

Aby uzyskać więcej informacji, zobacz [IDataObject::EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) w sdk systemu Windows.

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject::COleDataObject

Konstruuje `COleDataObject` obiekt.

```
COleDataObject();
```

### <a name="remarks"></a>Uwagi

Wywołanie [COleDataObject::Attach](#attach) lub [COleDataObject::AttachClipboard](#attachclipboard) musi zostać `COleDataObject` wykonane przed wywołaniem innych funkcji.

> [!NOTE]
> Ponieważ jednym z parametrów do obsługi przeciągania i `COleDataObject`upuszczania jest wskaźnik do , nie ma potrzeby wywoływania tego konstruktora do obsługi przeciągania i upuszczania.

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleDataObject::Detach

Wywołanie tej funkcji, `COleDataObject` aby odłączyć obiekt od skojarzonego obiektu danych OLE bez zwalniania obiektu danych.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu danych OLE, który został odłączony.

### <a name="remarks"></a>Uwagi

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject::GetData

Wywołanie tej funkcji, aby pobrać dane z elementu w określonym formacie.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format, w którym mają być zwracane dane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwróconą przez natywną funkcję Windows [RegisterClipboardFormatat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpStgMedium*<br/>
Wskazuje na strukturę [STGMEDIUM,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) która będzie odbierać dane.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym mają być zwracane dane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie poza formatem Schowka określonym przez *cfFormat*. Jeśli jest null, wartości domyślne są używane `FORMATETC` dla innych pól w strukturze.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w windows SDK.

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject::GetFileData

Wywołanie tej funkcji, aby utworzyć `CFile` lub `CFile`-pochodne obiektu i `CFile` pobrać dane w określonym formacie do wskaźnika.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format, w którym mają być zwracane dane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwróconą przez natywną funkcję Windows [RegisterClipboardFormatat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym mają być zwracane dane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie poza formatem Schowka określonym przez *cfFormat*. Jeśli jest null, wartości domyślne są używane `FORMATETC` dla innych pól w strukturze.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CFile` nowego `CFile`lub pochodnego obiektu zawierającego dane, jeśli się powiedzie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

W zależności od nośnika, na jakim są przechowywane dane, `CFile`rzeczywisty typ wskazywał przez zwracaną wartość może być , `CSharedFile`lub `COleStreamFile`.

> [!NOTE]
> Obiekt, `CFile` do którego ma dostęp zwracana wartość tej funkcji, jest własnością obiektu wywołującego. Jest odpowiedzialny za obiekt wywołujący, `CFile` aby **usunąć** obiekt, zamykając w ten sposób plik.

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w windows SDK.

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject::GetGlobalData

Wywołanie tej funkcji, aby przydzielić globalny blok pamięci i pobrać dane w określonym formacie do HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format, w którym mają być zwracane dane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwróconą przez natywną funkcję Windows [RegisterClipboardFormatat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym mają być zwracane dane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie poza formatem Schowka określonym przez *cfFormat*. Jeśli jest null, wartości domyślne są używane `FORMATETC` dla innych pól w strukturze.

### <a name="return-value"></a>Wartość zwracana

Dojście globalnego bloku pamięci zawierającego dane, jeśli zakończy się pomyślnie; w przeciwnym razie NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w windows SDK.

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject::GetNextFormat

Wywołanie tej funkcji wielokrotnie, aby uzyskać wszystkie formaty dostępne do pobierania danych z elementu.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC,](/windows/win32/api/objidl/ns-objidl-formatetc) która odbiera informacje o formacie, gdy zwraca wywołanie funkcji.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli inny format jest dostępny; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po wywołaniu [COleDataObject::BeginEnumFormats](#beginenumformats), pozycja pierwszego formatu obsługiwanego przez ten obiekt danych jest przechowywana. Kolejne wywołania `GetNextFormat` wyliczą listę dostępnych formatów w obiekcie danych. Użyj tych funkcji, aby wyświetlić listę dostępnych formatów.

Aby sprawdzić dostępność danego formatu, zadzwoń [COleDataObject::IsDataAvailable](#isdataavailable).

Aby uzyskać więcej informacji, zobacz [IEnumXXXX::Next](/previous-versions//ms695273\(v=vs.85\)) w windows SDK.

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject::IsDataDostępne

Wywołanie tej funkcji, aby ustalić, czy określony format jest dostępny do pobierania danych z elementu OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format danych Schowka do użycia w strukturze wskazywowej przez *lpFormatEtc*. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwróconą przez natywną funkcję Windows [RegisterClipboardFormatat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą żądany format. Podaj wartość tego parametru tylko wtedy, gdy chcesz określić dodatkowe informacje o formacie poza formatem Schowka określonym przez *cfFormat*. Jeśli jest null, wartości domyślne są używane `FORMATETC` dla innych pól w strukturze.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli dane są dostępne w określonym formacie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest `GetData`przydatna `GetFileData`przed `GetGlobalData`wywołaniem , lub .

Aby uzyskać więcej informacji, zobacz [IDataObject::QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w usłudze Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

## <a name="coledataobjectrelease"></a><a name="release"></a>COleDataObject::Release COleDataObject::Release COleDataObject::Release COle

Wywołanie tej funkcji, aby zwolnić własność [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) obiektu, `COleDataObject` który był wcześniej skojarzony z obiektem.

```
void Release();
```

### <a name="remarks"></a>Uwagi

Był `IDataObject` skojarzony z `COleDataObject` `Attach` wywołaniem `AttachClipboard` lub jawnie lub przez ramy. Jeśli parametr *bAutoRelease* jest `Attach` FALSE, `IDataObject` obiekt nie zostanie zwolniony. W takim przypadku wywołujący jest odpowiedzialny `IDataObject` za zwolnienie przez wywołanie [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDataSource](../../mfc/reference/coledatasource-class.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)
