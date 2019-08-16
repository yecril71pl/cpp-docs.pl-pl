---
title: Klasa by uzyskać COleDataSource
ms.date: 11/04/2016
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
ms.openlocfilehash: 5e6b49edfedc8e7311e9ecc21ca065ad99c15c62
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504131"
---
# <a name="coledatasource-class"></a>Klasa by uzyskać COleDataSource

Działa jako pamięć podręczna, w której aplikacja umieszcza dane, które będą oferowane podczas operacji transferu danych, takich jak schowek lub operacje przeciągania i upuszczania.

## <a name="syntax"></a>Składnia

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[By uzyskać COleDataSource:: by uzyskać COleDataSource](#coledatasource)|Konstruuje `COleDataSource` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[By uzyskać COleDataSource:: CacheData](#cachedata)|Oferuje dane w określonym formacie przy użyciu `STGMEDIUM` struktury.|
|[By uzyskać COleDataSource:: CacheGlobalData](#cacheglobaldata)|Oferuje dane w określonym formacie za pomocą HGLOBAL.|
|[By uzyskać COleDataSource::D elayRenderData](#delayrenderdata)|Oferuje dane w określonym formacie za pomocą opóźnionego renderowania.|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Oferuje dane w określonym formacie we `CFile` wskaźniku.|
|[By uzyskać COleDataSource::D elaySetData](#delaysetdata)|Wywoływana dla każdego formatu obsługiwanego w programie `OnSetData`.|
|[By uzyskać COleDataSource::D oDragDrop](#dodragdrop)|Wykonuje operacje przeciągania i upuszczania ze źródłem danych.|
|[By uzyskać COleDataSource:: Empty](#empty)|`COleDataSource` Opróżnia obiekt danych.|
|[By uzyskać COleDataSource:: FlushClipboard](#flushclipboard)|Renderuje wszystkie dane do Schowka.|
|[By uzyskać COleDataSource:: GetClipboardOwner](#getclipboardowner)|Sprawdza, czy w tym miejscu znajdują się dane umieszczone w Schowku.|
|[By uzyskać COleDataSource:: OnRenderData](#onrenderdata)|Pobiera dane w ramach opóźnionego renderowania.|
|[By uzyskać COleDataSource:: OnRenderFileData](#onrenderfiledata)|Pobiera dane do elementu `CFile` jako część opóźnionego renderowania.|
|[By uzyskać COleDataSource:: OnRenderGlobalData](#onrenderglobaldata)|Pobiera dane do HGLOBAL w ramach opóźnionego renderowania.|
|[By uzyskać COleDataSource:: OnSetData](#onsetdata)|Wywołuje się, by zastąpić dane w `COleDataSource` obiekcie.|
|[By uzyskać COleDataSource:: setClipboard](#setclipboard)|`COleDataSource` Umieszcza obiekt w Schowku.|

## <a name="remarks"></a>Uwagi

Źródła danych OLE można tworzyć bezpośrednio. Alternatywnie klasy [COleClientItem](../../mfc/reference/coleclientitem-class.md) i [COleServerItem](../../mfc/reference/coleserveritem-class.md) tworzą źródła danych OLE w odpowiedzi na ich `CopyToClipboard` funkcje i `DoDragDrop` elementy członkowskie. Aby uzyskać krótki opis, zobacz [COleServerItem:: CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) . Przesłoń funkcję `CopyToClipboard` `DoDragDrop` członkowską elementu klienta lub klasy elementu serwera, aby dodać do danych dodatkowe formaty schowka, które zostały utworzone dla lub funkcji członkowskiej. `OnGetClipboardData`

Za każdym razem, gdy chcesz przygotować dane do przeniesienia, należy utworzyć obiekt tej klasy i wypełnić go danymi przy użyciu najbardziej odpowiedniej metody dla danych. Sposób, w jaki jest wstawiany do źródła danych, jest bezpośrednio narażony na to, czy dane są dostarczane natychmiast (bezpośrednie renderowanie) czy na żądanie (opóźnione renderowanie). Dla każdego formatu Schowka, w którym dane są przekazywane, przekazując format schowka do użycia (i opcjonalną strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) ), wywołaj [DelayRenderData](#delayrenderdata).

Aby uzyskać więcej informacji o źródłach danych i transferze danych, zobacz temat [obiekty danych artykułu i źródła danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Ponadto w artykule [schowek](../../mfc/clipboard.md) artykułu opisano mechanizm Schowka OLE.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** Afxole. h

##  <a name="cachedata"></a>By uzyskać COleDataSource:: CacheData

Wywołaj tę funkcję, aby określić format, w którym dane są oferowane podczas operacji transferu danych.

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format schowka, w którym mają być oferowane dane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwracaną przez natywną funkcję [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) systemu Windows.

*lpStgMedium*<br/>
Wskazuje strukturę [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) zawierającą dane w określonym formacie.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym mają być oferowane dane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie spoza formatu Schowka określonego przez *cfFormat*. Jeśli ma wartość null, są używane wartości domyślne dla innych pól `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

Należy podać dane, ponieważ ta funkcja udostępnia je za pomocą natychmiastowego renderowania. Dane są zapisywane w pamięci podręcznej, dopóki nie będzie trzeba.

Podaj dane przy użyciu struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) . Możesz również użyć funkcji członkowskiej, `CacheGlobalData` Jeśli ilość danych, które dostarczasz, jest wystarczająco mała, aby można było ją efektywnie przenieść przy użyciu HGLOBAL.

`CacheData` Po wywołaniu `ptd` elementu członkowskiego `lpFormatEtc` i treści *lpStgMedium* są własnością obiektu danych, a nie przez wywołującego.

Aby użyć renderowania opóźnionego, wywołaj funkcję członkowską [DelayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) . Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsługiwanego przez MFC [, zapoznaj się z tematem obiekty danych artykułu i źródła danych: Manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w Windows SDK.

##  <a name="cacheglobaldata"></a>By uzyskać COleDataSource:: CacheGlobalData

Wywołaj tę funkcję, aby określić format, w którym dane są oferowane podczas operacji transferu danych.

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format schowka, w którym mają być oferowane dane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwracaną przez natywną funkcję [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) systemu Windows.

*hGlobal*<br/>
Dojście do bloku pamięci globalnej zawierające dane w określonym formacie.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym mają być oferowane dane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie spoza formatu Schowka określonego przez *cfFormat*. Jeśli ma wartość null, są używane wartości domyślne dla innych pól `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

Ta funkcja udostępnia dane za pomocą bezpośredniego renderowania, dlatego należy podać dane podczas wywoływania funkcji; dane są zapisywane w pamięci podręcznej, dopóki nie będzie trzeba. Użyj funkcji `CacheData` członkowskiej, jeśli dostarczasz dużą ilość danych lub potrzebujesz strukturalnego nośnika magazynu.

Aby użyć renderowania opóźnionego, wywołaj funkcję członkowską [DelayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) . Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsługiwanego przez MFC [, zapoznaj się z tematem obiekty danych artykułu i źródła danych: Manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w Windows SDK.

##  <a name="coledatasource"></a>By uzyskać COleDataSource:: by uzyskać COleDataSource

Konstruuje `COleDataSource` obiekt.

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>By uzyskać COleDataSource::D elayRenderData

Wywołaj tę funkcję, aby określić format, w którym dane są oferowane podczas operacji transferu danych.

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format schowka, w którym mają być oferowane dane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwracaną przez natywną funkcję [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) systemu Windows.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym mają być oferowane dane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie spoza formatu Schowka określonego przez *cfFormat*. Jeśli ma wartość null, są używane wartości domyślne dla innych pól `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

Ta funkcja udostępnia dane przy użyciu opóźnionego renderowania, więc dane nie są dostarczane od razu. Funkcja członkowska [OnRenderData](#onrenderdata) lub [OnRenderGlobalData](#onrenderglobaldata) jest wywoływana w celu zażądania danych.

Użyj tej funkcji, jeśli nie chcesz podawać danych za pośrednictwem `CFile` obiektu. Jeśli chcesz dostarczyć dane za pośrednictwem `CFile` obiektu, wywołaj funkcję elementu członkowskiego [DelayRenderFileData](#delayrenderfiledata) . Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsługiwanego przez MFC [, zapoznaj się z tematem obiekty danych artykułu i źródła danych: Manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby użyć bezpośredniego renderowania, wywołaj funkcję członkowską [CacheData](#cachedata) lub [CacheGlobalData](#cacheglobaldata) .

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w Windows SDK.

##  <a name="delayrenderfiledata"></a>By uzyskać COleDataSource::D elayRenderFileData

Wywołaj tę funkcję, aby określić format, w którym dane są oferowane podczas operacji transferu danych.

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format schowka, w którym mają być oferowane dane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwracaną przez natywną funkcję [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) systemu Windows.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym mają być oferowane dane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie spoza formatu Schowka określonego przez *cfFormat*. Jeśli ma wartość null, są używane wartości domyślne dla innych pól `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

Ta funkcja udostępnia dane przy użyciu opóźnionego renderowania, więc dane nie są dostarczane od razu. Funkcja członkowska [OnRenderFileData](#onrenderfiledata) jest wywoływana w celu zażądania danych.

Użyj tej funkcji, jeśli zamierzasz użyć `CFile` obiektu do dostarczenia danych. Jeśli nie zamierzasz używać `CFile` obiektu, wywołaj funkcję elementu członkowskiego [DelayRenderData](#delayrenderdata) . Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsługiwanego przez MFC [, zapoznaj się z tematem obiekty danych artykułu i źródła danych: Manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby użyć bezpośredniego renderowania, wywołaj funkcję członkowską [CacheData](#cachedata) lub [CacheGlobalData](#cacheglobaldata) .

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w Windows SDK.

##  <a name="delaysetdata"></a>By uzyskać COleDataSource::D elaySetData

Wywołaj tę funkcję, aby obsłużyć zmianę zawartości źródła danych.

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format schowka, w którym mają zostać umieszczone dane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwracaną przez natywną funkcję [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) systemu Windows.

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym mają zostać zamienione dane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie spoza formatu Schowka określonego przez *cfFormat*. Jeśli ma wartość null, są używane wartości domyślne dla innych pól `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

[](#onsetdata) Wywołanie OnSetData zostanie wywołane przez platformę, gdy wystąpi taka sytuacja. Jest on używany tylko wtedy, gdy struktura zwraca źródło danych z [COleServerItem:: GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Jeśli `DelaySetData` nie jest wywoływana `OnSetData` , funkcja nigdy nie będzie wywoływana. `DelaySetData`należy wywołać dla każdego obsługiwanego schowka `FORMATETC` lub formatu.

Aby uzyskać więcej informacji, zapoznaj się ze strukturą [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w Windows SDK.

##  <a name="dodragdrop"></a>By uzyskać COleDataSource::D oDragDrop

Wywołaj funkcję [](../../mfc/reference/cwnd-class.md#onlbuttondown) elementuczłonkowskiego,abywykonaćoperacjęprzeciąganiaiupuszczaniadlategoźródładanych,zwyklewprogramieobsługiCWnd::`DoDragDrop` OnLButtonDown.

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parametry

*dwEffects*<br/>
Operacje przeciągania i upuszczania, które są dozwolone w tym źródle danych. Może to być jeden lub więcej z następujących elementów:

- DROPEFFECT_COPY można wykonać operacji kopiowania.

- DROPEFFECT_MOVE można wykonać operacji przenoszenia.

- DROPEFFECT_LINK łącze z usuniętych danych do oryginalnych danych.

- DROPEFFECT_SCROLL wskazuje, że może wystąpić przeciąganie operacji przewijania.

*lpRectStartDrag*<br/>
Wskaźnik do prostokąta, który definiuje, gdzie w rzeczywistości zostanie rozpoczęte przeciąganie. Aby uzyskać więcej informacji zobacz następujące sekcji uwag.

*pDropSource*<br/>
Wskazuje na źródło upuszczania. Jeśli wartość jest równa NULL, zostanie użyta domyślna implementacja [COleDropSource](../../mfc/reference/coledropsource-class.md) .

### <a name="return-value"></a>Wartość zwracana

Efekt upuszczania wygenerowany przez operację przeciągania i upuszczania; w przeciwnym razie DROPEFFECT_NONE, jeśli operacja nie rozpocznie się, ponieważ użytkownik wydał przycisk myszy przed opuszczeniem dostarczonego prostokąta.

### <a name="remarks"></a>Uwagi

Operacja przeciągania i upuszczania nie rozpocznie się natychmiast. Czeka, aż kursor myszy opuści prostokąt określony przez *lpRectStartDrag* lub dopóki nie upłynie określona liczba milisekund. Jeśli *lpRectStartDrag* ma wartość null, rozmiar prostokąta wynosi jeden piksel.

Czas opóźnienia jest określany przez ustawienie klucza rejestru. Można zmienić czas opóźnienia przez wywołanie [CWinApp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) lub [CWinApp:: WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Jeśli czas opóźnienia nie zostanie określony, zostanie użyta wartość domyślna 200 milisekund. Czas opóźnienia przeciągania jest przechowywany w następujący sposób:

- Czas opóźnienia przeciągania systemu Windows NT jest przechowywany w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Czas opóźnienia przeciągania systemu Windows 3. x jest przechowywany w WIN. Plik INI, w sekcji [Windows}.

- Czas opóźnienia przeciągania systemu Windows 95/98 jest przechowywany w pamięci podręcznej w wersji zakupionej. Nośnika.

Aby uzyskać więcej informacji na temat sposobu przechowywania informacji o opóźnieniu przeciągania w rejestrze lub. Plik INI, zobacz [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) w Windows SDK.

Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie źródła](../../mfc/drag-and-drop-implementing-a-drop-source.md)upuszczania.

##  <a name="empty"></a>By uzyskać COleDataSource:: Empty

Wywołaj tę funkcję, aby `COleDataSource` opróżnić obiekt danych.

```
void Empty();
```

### <a name="remarks"></a>Uwagi

Buforowane i opóźnione formaty renderowania są opróżniane, aby mogły być ponownie używane.

Aby uzyskać więcej informacji, zobacz [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) w Windows SDK.

##  <a name="flushclipboard"></a>By uzyskać COleDataSource:: FlushClipboard

Renderuje dane znajdujące się w schowku, a następnie umożliwia wklejanie danych ze schowka po zamknięciu aplikacji.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Uwagi

Użyj [setClipboard](#setclipboard) , aby umieścić dane w Schowku.

##  <a name="getclipboardowner"></a>By uzyskać COleDataSource:: GetClipboardOwner

Określa, czy dane ze schowka uległy zmianie od [](#setclipboard) czasu ostatniego wywołania programu setClipboard i, jeśli tak, identyfikują bieżącego właściciela.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Wartość zwracana

Źródło danych znajdujące się obecnie w schowku lub ma wartość NULL, jeśli nie ma niczego w schowku lub jeśli Schowek nie należy do aplikacji wywołującej.

##  <a name="onrenderdata"></a>By uzyskać COleDataSource:: OnRenderData

Wywoływane przez platformę, by pobrać dane w określonym formacie.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , określając format, w którym informacje są żądane.

*lpStgMedium*<br/>
Wskazuje strukturę [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) , w której mają zostać zwrócone dane.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format jest jednym wcześniej umieszczonym w `COleDataSource` obiekcie przy użyciu funkcji składowej [DelayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) na potrzeby opóźnionego renderowania. Domyślna implementacja tej funkcji wywoła [OnRenderFileData](#onrenderfiledata) lub [OnRenderGlobalData](#onrenderglobaldata) , jeśli dostarczony nośnik magazynu jest odpowiednio plikiem lub pamięcią. Jeśli żaden z tych formatów nie zostanie podany, domyślna implementacja zwróci wartość 0 i nic nie rób. Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsługiwanego przez MFC [, zapoznaj się z tematem obiekty danych artykułu i źródła danych: Manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Jeśli *lpStgMedium*-> *TYMED jest* TYMED_NULL, powinnobyćprzydzieloneiwypełnianejakookreśloneprzezlpFormatEtc->TYMED.`STGMEDIUM` Jeśli nie jest to TYMED_NULL, `STGMEDIUM` należy wypełnić dane.

Jest to zaawansowany możliwy do zaawansowania. Zastąp tę funkcję, aby dostarczyć dane w żądanym formacie i średnim. W zależności od danych warto zamiast tego zastąpić jedną z innych wersji tej funkcji. Jeśli dane są małe i stały się w rozmiarze, Przesłoń `OnRenderGlobalData`. Jeśli dane są w pliku lub mają zmienny rozmiar, Przesłoń `OnRenderFileData`.

Aby uzyskać więcej informacji, zobacz struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , typ wyliczenia [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) i [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w Windows SDK.

##  <a name="onrenderfiledata"></a>By uzyskać COleDataSource:: OnRenderFileData

Wywoływane przez platformę, by pobrać dane w określonym formacie, gdy określony nośnik magazynu jest plikiem.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , określając format, w którym informacje są żądane.

*pFile*<br/>
Wskazuje obiekt [CFile](../../mfc/reference/cfile-class.md) , w którym mają być renderowane dane.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format jest jednym wcześniej umieszczonym w `COleDataSource` obiekcie przy użyciu funkcji składowej [DelayRenderData](#delayrenderdata) do opóźnionego renderowania. Domyślna implementacja tej funkcji po prostu zwraca wartość FALSE.

Jest to zaawansowany możliwy do zaawansowania. Zastąp tę funkcję, aby dostarczyć dane w żądanym formacie i średnim. W zależności od danych warto zamiast tego zastąpić jedną z innych wersji tej funkcji. Jeśli chcesz obsłużyć wiele nośników magazynu, Przesłoń [OnRenderData](#onrenderdata). Jeśli dane są w pliku lub mają zmienny rozmiar, Przesłoń `OnRenderFileData`. Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsługiwanego przez MFC [, zapoznaj się z tematem obiekty danych artykułu i źródła danych: Manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) i [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w Windows SDK.

##  <a name="onrenderglobaldata"></a>By uzyskać COleDataSource:: OnRenderGlobalData

Wywoływane przez platformę, aby pobrać dane w określonym formacie, gdy określony nośnik magazynu ma pamięć globalną.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , określając format, w którym informacje są żądane.

*phGlobal*<br/>
Wskazuje dojście do pamięci globalnej, w której mają zostać zwrócone dane. Jeśli jeden z nich nie został jeszcze przydzielony, ten parametr może mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format jest jednym wcześniej umieszczonym w `COleDataSource` obiekcie przy użyciu funkcji składowej [DelayRenderData](#delayrenderdata) do opóźnionego renderowania. Domyślna implementacja tej funkcji po prostu zwraca wartość FALSE.

Jeśli *phGlobal* ma wartość null, należy alokować i zwrócić nową HGLOBAL w *phGlobal*. W przeciwnym razie HGLOBAL określona przez *phGlobal* powinna być wypełniony danymi. Ilość danych umieszczonych w HGLOBAL nie może przekraczać bieżącego rozmiaru bloku pamięci. Ponadto nie można zmienić przydziału bloku na większy rozmiar.

Jest to zaawansowany możliwy do zaawansowania. Zastąp tę funkcję, aby dostarczyć dane w żądanym formacie i średnim. W zależności od danych warto zamiast tego zastąpić jedną z innych wersji tej funkcji. Jeśli chcesz obsłużyć wiele nośników magazynu, Przesłoń [OnRenderData](#onrenderdata). Jeśli dane są w pliku lub mają zmienny rozmiar, Przesłoń [OnRenderFileData](#onrenderfiledata). Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsługiwanego przez MFC [, zapoznaj się z tematem obiekty danych artykułu i źródła danych: Manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) i [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w Windows SDK.

##  <a name="onsetdata"></a>By uzyskać COleDataSource:: OnSetData

Wywoływane przez platformę w celu ustawienia lub zastąpienia danych w `COleDataSource` obiekcie w określonym formacie.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) , określając format, w którym są zastępowane dane.

*lpStgMedium*<br/>
Wskazuje strukturę [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) zawierającą dane, które zastąpią bieżącą zawartość `COleDataSource` obiektu.

*bRelease*<br/>
Wskazuje, kto ma własność nośnika magazynu po zakończeniu wywołania funkcji. Obiekt wywołujący decyduje, kto jest odpowiedzialny za wydanie zasobów przyznanych w imieniu nośnika magazynu. Obiekt wywołujący robi to przez ustawienie *bRelease*. Jeśli *bRelease* ma wartość różną od zera, źródłem danych jest własność, zwalniając nośnik po zakończeniu jego używania. Gdy *bRelease* jest równa 0, wywołujący zachowuje własność, a źródło danych może używać nośnika magazynu tylko dla czasu trwania wywołania.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Źródło danych nie przejmuje własności danych do momentu jego pomyślnego uzyskania. Oznacza to, że nie przyjmuje własności, jeśli `OnSetData` zwraca wartość 0. Jeśli źródło danych przejmuje własność, zwalnia nośnik magazynu przez wywołanie funkcji [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) .

Domyślna implementacja nie robi nic. Zastąp tę funkcję, aby zastąpić dane w określonym formacie. Jest to zaawansowany możliwy do zaawansowania.

Aby uzyskać więcej informacji, zobacz struktury [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-stgmedium) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) oraz [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) i [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w Windows SDK.

##  <a name="setclipboard"></a>By uzyskać COleDataSource:: setClipboard

Umieszcza dane zawarte w `COleDataSource` obiekcie w Schowku po wywołaniu jednej z następujących funkcji: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata)lub [DelayRenderFileData](#delayrenderfiledata).

```
void SetClipboard();
```

## <a name="see-also"></a>Zobacz także

[Przykład HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Przykład OCLIENT MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDataObject](../../mfc/reference/coledataobject-class.md)
