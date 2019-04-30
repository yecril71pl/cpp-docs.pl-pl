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
ms.openlocfilehash: 24d79c684226d57839161946255781c3bdd5a043
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341702"
---
# <a name="coledataobject-class"></a>Klasa COleDataObject

Używany podczas transferu danych dla pobierania danych w różnych formatach, ze Schowka, za pomocą przeciągania i upuszczania, lub z wbudowanego elementu OLE.

## <a name="syntax"></a>Składnia

```
class COleDataObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|Konstruuje `COleDataObject` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDataObject::Attach](#attach)|Dołącza określony obiekt danych OLE do `COleDataObject`.|
|[COleDataObject::AttachClipboard](#attachclipboard)|Dołącza obiekt danych do Schowka.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Przygotowuje dla jednego lub więcej kolejnych `GetNextFormat` wywołania.|
|[COleDataObject::Detach](#detach)|Odłącza skojarzony `IDataObject` obiektu.|
|[COleDataObject::GetData](#getdata)|Kopiuje dane z przyłączonego obiektu OLE w danych, w określonym formacie.|
|[COleDataObject::GetFileData](#getfiledata)|Kopiuje dane z przyłączonego obiektu OLE w danych, do `CFile` wskaźnika w określonym formacie.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Kopiuje dane z przyłączonego obiektu OLE w danych, do `HGLOBAL` w określonym formacie.|
|[COleDataObject::GetNextFormat](#getnextformat)|Zwraca następny dostępny format danych.|
|[COleDataObject::IsDataAvailable](#isdataavailable)|Sprawdza, czy dane są dostępne w określonym formacie.|
|[COleDataObject::Release](#release)|Powoduje odłączenie i zwalnia skojarzonego `IDataObject` obiektu.|

## <a name="remarks"></a>Uwagi

`COleDataObject` nie ma klasy bazowej.

Tego rodzaju transfery danych obejmują źródło i miejsce docelowe. Źródło danych jest implementowany jako obiekt [COleDataSource](../../mfc/reference/coledatasource-class.md) klasy. Zawsze, gdy aplikacji docelowej został porzucony w nim danych lub jest monit o wykonanie operacji wklejania ze Schowka obiektu `COleDataObject` klasy musi zostać utworzona.

Ta klasa umożliwia określenie, czy dane istnieje w określonym formacie. Można również wyliczyć dostępnych formatów danych lub sprawdź, czy dany format jest dostępny, a następnie pobrać dane w preferowanym formacie. Pobieranie obiektu można zrobić na kilka różnych sposobów, łącznie z użyciem [CFile](../../mfc/reference/cfile-class.md), moduł wartości HGLOBAL lub moduł `STGMEDIUM` struktury.

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji o korzystaniu z obiektów danych w aplikacji, zobacz artykuł [obiekty danych i źródeł danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`COleDataObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="attach"></a>  COleDataObject::Attach

Wywołaj tę funkcję, aby skojarzyć `COleDataObject` obiektu z obiektu danych.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parametry

*lpDataObject*<br/>
Wskazuje obiektu danych.

*bAutoRelease*<br/>
Wartość TRUE, jeśli obiekt danych OLE powinien być zwolnione, kiedy `COleDataObject` obiekt jest niszczone; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) w zestawie Windows SDK.

##  <a name="attachclipboard"></a>  COleDataObject::AttachClipboard

Wywołaj tę funkcję, aby dołączyć obiekt danych, który jest aktualnie w Schowka w celu `COleDataObject` obiektu.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Wywołanie tej funkcji umożliwia zablokowanie Schowka, dopóki ten obiekt danych jest zwalniany. Obiekt danych jest publikowany w destruktor dla `COleDataObject`. Aby uzyskać więcej informacji, zobacz [Funkcja OpenClipboard](/windows/desktop/api/winuser/nf-winuser-openclipboard) i [Funkcja CloseClipboard](/windows/desktop/api/winuser/nf-winuser-closeclipboard) w dokumentacji systemu Win32.

##  <a name="beginenumformats"></a>  COleDataObject::BeginEnumFormats

Wywołaj tę funkcję, aby przygotować się do kolejnych wywołań `GetNextFormat` do pobierania listy formatów danych z elementu.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Uwagi

Po wywołaniu `BeginEnumFormats`, znajduje się pozycja pierwszego format, obsługiwany przez ten obiekt danych. Kolejne wywołania `GetNextFormat` wylicza listę dostępnych formatów w obiekcie danych.

Aby sprawdzić dostępność danych w danym formacie, należy użyć [COleDataObject::IsDataAvailable](#isdataavailable).

Aby uzyskać więcej informacji, zobacz [IDataObject::EnumFormatEtc](/windows/desktop/api/objidl/nf-objidl-idataobject-enumformatetc) w zestawie Windows SDK.

##  <a name="coledataobject"></a>  COleDataObject::COleDataObject

Konstruuje `COleDataObject` obiektu.

```
COleDataObject();
```

### <a name="remarks"></a>Uwagi

Wywołanie [COleDataObject::Attach](#attach) lub [COleDataObject::AttachClipboard](#attachclipboard) musi nastąpić przed wywołaniem innych `COleDataObject` funkcji.

> [!NOTE]
>  Ponieważ jeden z parametrów do obsługi przeciągania i upuszczania jest wskaźnikiem do `COleDataObject`, nie ma potrzeby do wywołania tego konstruktora do obsługi przeciągania i upuszczania.

##  <a name="detach"></a>  COleDataObject::Detach

Wywołaj tę funkcję, aby odłączyć `COleDataObject` obiekt z jego skojarzonego obiektu danych OLE bez zwalniania obiektu danych.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu danych OLE, która została odłączona.

### <a name="remarks"></a>Uwagi

##  <a name="getdata"></a>  COleDataObject::GetData

Wywołaj tę funkcję, aby pobrać dane z elementu w określonym formacie.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format, w którym ma zostać zwrócone dane. Ten parametr może być jednym z wstępnie zdefiniowane formaty Schowka lub wartość zwrócona przez obiekt natywny Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji.

*lpStgMedium*<br/>
Wskazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) strukturę, która będzie odbierać dane.

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury opisujący format, w którym ma zostać zwrócone dane. Podaj wartość dla tego parametru, jeśli chcesz określić informacji o formacie dodatkowe poza określonym przez format schowka *cfFormat*. Jeśli ma wartość NULL, wartości domyślne są używane dla innych pól w `FORMATETC` struktury.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Metoda IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium), i [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w zestawie Windows SDK.

##  <a name="getfiledata"></a>  COleDataObject::GetFileData

Wywołaj tę funkcję, aby utworzyć `CFile` lub `CFile`-pochodnych obiektu oraz do pobierania danych w określonym formacie do `CFile` wskaźnika.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format, w którym ma zostać zwrócone dane. Ten parametr może być jednym z wstępnie zdefiniowane formaty Schowka lub wartość zwrócona przez obiekt natywny Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji.

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury opisujący format, w którym ma zostać zwrócone dane. Podaj wartość dla tego parametru, jeśli chcesz określić informacji o formacie dodatkowe poza określonym przez format schowka *cfFormat*. Jeśli ma wartość NULL, wartości domyślne są używane dla innych pól w `FORMATETC` struktury.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowego `CFile` lub `CFile`-pochodzi obiekt zawierający dane, jeśli operacja się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

W zależności od średniej, dane są przechowywane w, może być rzeczywisty typ wskazywany przez wartość zwracaną `CFile`, `CSharedFile`, lub `COleStreamFile`.

> [!NOTE]
>  `CFile` Przez obiekt wywołujący właścicielem jest obiekt dostępne przez wartość zwracana przez tę funkcję. Jest odpowiedzialny za obiekt wywołujący, aby **Usuń** `CFile` obiektu, a tym samym zamyka plik.

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w zestawie Windows SDK.

##  <a name="getglobaldata"></a>  COleDataObject::GetGlobalData

Wywołaj tę funkcję można przydzielić bloku pamięci globalnej oraz do pobierania danych w określonym formacie do wartości HGLOBAL.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format, w którym ma zostać zwrócone dane. Ten parametr może być jednym z wstępnie zdefiniowane formaty Schowka lub wartość zwrócona przez obiekt natywny Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji.

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury opisujący format, w którym ma zostać zwrócone dane. Podaj wartość dla tego parametru, jeśli chcesz określić informacji o formacie dodatkowe poza określonym przez format schowka *cfFormat*. Jeśli ma wartość NULL, wartości domyślne są używane dla innych pól w `FORMATETC` struktury.

### <a name="return-value"></a>Wartość zwracana

Dojście do bloku pamięci globalnej, zawierające dane, jeśli to się powiedzie; w przeciwnym razie wartość NULL.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w zestawie Windows SDK.

##  <a name="getnextformat"></a>  COleDataObject::GetNextFormat

Wywołaj tę funkcję, wielokrotnie, aby uzyskać wszystkie formaty dostępne do pobrania danych z elementu.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) strukturę, która otrzymuje informacje w formacie, gdy wywołanie funkcji zwraca.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli inny format jest dostępna; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Po wywołaniu [COleDataObject::BeginEnumFormats](#beginenumformats), znajduje się pozycja pierwszego format, obsługiwany przez ten obiekt danych. Kolejne wywołania `GetNextFormat` wylicza listę dostępnych formatów w obiekcie danych. Użyj tych funkcji, aby wyświetlić listę dostępnych formatów.

Aby sprawdzić dostępność danego formatu, należy wywołać [COleDataObject::IsDataAvailable](#isdataavailable).

Aby uzyskać więcej informacji, zobacz [IEnumXXXX::Next](https://msdn.microsoft.com/library/ms695273.aspx) w zestawie Windows SDK.

##  <a name="isdataavailable"></a>  COleDataObject::IsDataAvailable

Wywołaj tę funkcję, aby ustalić, czy określonego formatu jest dostępna do pobrania danych z elementu OLE.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Formatu danych schowka do użycia w strukturze wskazywany przez *lpFormatEtc*. Ten parametr może być jednym z wstępnie zdefiniowane formaty Schowka lub wartość zwrócona przez obiekt natywny Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji.

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) opisujący format żądanego struktury. Podaj wartość dla tego parametru, tylko wtedy, gdy chcesz określić informacji o formacie dodatkowe poza określonym przez format schowka *cfFormat*. Jeśli ma wartość NULL, wartości domyślne są używane dla innych pól w `FORMATETC` struktury.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dane są dostępne w określonym formacie. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Funkcja ta jest przydatna przed wywołaniem `GetData`, `GetFileData`, lub `GetGlobalData`.

Aby uzyskać więcej informacji, zobacz [IDataObject::QueryGetData](/windows/desktop/api/objidl/nf-objidl-idataobject-querygetdata) i [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w zestawie Windows SDK.

### <a name="example"></a>Przykład

  Zobacz przykład [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

##  <a name="release"></a>  COleDataObject::Release

Wywołaj tę funkcję, aby zwolnić własności [IDataObject](/windows/desktop/api/objidl/nn-objidl-idataobject) obiekt, który był wcześniej skojarzony z `COleDataObject` obiektu.

```
void Release();
```

### <a name="remarks"></a>Uwagi

`IDataObject` Został skojarzony z `COleDataObject` przez wywołanie metody `Attach` lub `AttachClipboard` jawnie lub przez platformę. Jeśli *bAutoRelease* parametru `Attach` ma wartość FAŁSZ, `IDataObject` obiekt nie zostanie zwolniony. W tym przypadku obiekt wywołujący jest odpowiedzialny za przy zwalnianiu `IDataObject` przez wywołanie metody [IUnknown::Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release).

## <a name="see-also"></a>Zobacz także

[Próbki MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Próbki MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDataSource](../../mfc/reference/coledatasource-class.md)<br/>
[Klasa COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)
