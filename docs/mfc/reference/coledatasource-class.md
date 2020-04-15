---
title: Klasa COleDataSource
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
ms.openlocfilehash: fcf9505a7792aea6807e37f05cd1cb1aaad55830
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366120"
---
# <a name="coledatasource-class"></a>Klasa COleDataSource

Działa jako pamięć podręczna, w której aplikacja umieszcza dane, które będzie oferować podczas operacji transferu danych, takich jak Schowek lub operacji przeciągania i upuszczania.

## <a name="syntax"></a>Składnia

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Źródło COleDataSource::COleDataSource](#coledatasource)|Konstruuje `COleDataSource` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDataSource::CacheData](#cachedata)|Oferuje dane w określonym `STGMEDIUM` formacie przy użyciu struktury.|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Oferuje dane w określonym formacie za pomocą HGLOBAL.|
|[COleDataSource::DelayRenderData](#delayrenderdata)|Oferuje dane w określonym formacie przy użyciu opóźnionego renderowania.|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Oferuje dane w określonym `CFile` formacie w wskaźniku.|
|[COleDataSource::DelaySetData](#delaysetdata)|Wywoływana dla każdego formatu, który jest obsługiwany w `OnSetData`.|
|[COleDataSource::DoDragDrop](#dodragdrop)|Wykonuje operacje przeciągania i upuszczania ze źródłem danych.|
|[COleDataSource::Pusty](#empty)|Opróżnia `COleDataSource` obiekt danych.|
|[COleDataSource::FlushClipboard](#flushclipboard)|Renderuje wszystkie dane do Schowka.|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Sprawdza, czy dane umieszczone w Schowku nadal istnieją.|
|[COleDataSource::OnRenderData](#onrenderdata)|Pobiera dane w ramach opóźnionego renderowania.|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Pobiera dane do `CFile` jako część opóźnionego renderowania.|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Pobiera dane do HGLOBAL w ramach opóźnionego renderowania.|
|[COleDataSource::OnSetData](#onsetdata)|Wywoływana w celu `COleDataSource` zastąpienia danych w obiekcie.|
|[COleDataSource::SetClipboard](#setclipboard)|Umieszcza `COleDataSource` obiekt w Schowku.|

## <a name="remarks"></a>Uwagi

Źródła danych OLE można tworzyć bezpośrednio. Alternatywnie [COleClientItem](../../mfc/reference/coleclientitem-class.md) i [COleServerItem](../../mfc/reference/coleserveritem-class.md) klasy utworzyć źródła danych `CopyToClipboard` OLE `DoDragDrop` w odpowiedzi na ich i funkcji członkowskich. Zobacz [COleServerItem::CopyToClipboard,](../../mfc/reference/coleserveritem-class.md#copytoclipboard) aby uzyskać krótki opis. Zastąp `OnGetClipboardData` funkcję elementu członkowskiego elementu klienta lub klasy elementu serwera, aby dodać dodatkowe formaty `CopyToClipboard` `DoDragDrop` Schowka do danych w źródle danych OLE utworzonym dla funkcji lub elementu członkowskiego.

Za każdym razem, gdy chcesz przygotować dane do transferu, należy utworzyć obiekt tej klasy i wypełnić go danymi przy użyciu najbardziej odpowiedniej metody dla danych. Sposób, w jaki jest wstawiany do źródła danych, ma bezpośredni wpływ na to, czy dane są dostarczane natychmiast (natychmiastowe renderowanie) czy na żądanie (opóźnione renderowanie). Dla każdego formatu Schowka, w którym dostarczasz dane, przekazując format Schowka do użycia (i opcjonalną strukturę [FORMATETC),](/windows/win32/api/objidl/ns-objidl-formatetc) [wywołaj DelayRenderData](#delayrenderdata).

Aby uzyskać więcej informacji na temat źródeł danych i transferu danych, zobacz artykuł [Obiekty danych i źródła danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Ponadto w artykule [Tematy schowka](../../mfc/clipboard.md) opisano mechanizm Schowka OLE.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="coledatasourcecachedata"></a><a name="cachedata"></a>COleDataSource::CacheData

Wywołanie tej funkcji, aby określić format, w którym dane są oferowane podczas operacji transferu danych.

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym dane mają być oferowane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwróconą przez natywną funkcję Windows [RegisterClipboardFormatat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpStgMedium*<br/>
Wskazuje strukturę [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) zawierającą dane w określonym formacie.

*lpFormatEtc*<br/>
Wskazuje na strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym dane mają być oferowane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie poza formatem Schowka określonym przez *cfFormat*. Jeśli jest null, wartości domyślne są używane `FORMATETC` dla innych pól w strukturze.

### <a name="remarks"></a>Uwagi

Należy podać dane, ponieważ ta funkcja zapewnia je przy użyciu natychmiastowego renderowania. Dane są buforowane, dopóki nie są potrzebne.

Dostarczaj dane przy użyciu struktury [STGMEDIUM.](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) Można również użyć `CacheGlobalData` funkcji elementu członkowskiego, jeśli ilość danych, które dostarczasz jest wystarczająco mała, aby można było je sprawnie przesyłać za pomocą HGLOBAL.

Po wywołaniu `CacheData` `ptd` do `lpFormatEtc` członka i zawartość *lpStgMedium* są własnością obiektu danych, a nie przez obiekt wywołujący.

Aby użyć opóźnionego [renderowania, należy wywołać delayRenderData](#delayrenderdata) lub [DelayRenderFileData funkcji członkowskiej.](#delayrenderfiledata) Aby uzyskać więcej informacji na temat opóźnionego renderowania obsługiwanego przez MFC, zobacz artykuł [Obiekty danych i źródła danych: Manipulacja](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [struktury STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w sdk systemu Windows.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w windows SDK.

## <a name="coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a>COleDataSource::CacheGlobalData

Wywołanie tej funkcji, aby określić format, w którym dane są oferowane podczas operacji transferu danych.

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym dane mają być oferowane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwróconą przez natywną funkcję Windows [RegisterClipboardFormatat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*Hglobal*<br/>
Dojem do globalnego bloku pamięci zawierającego dane w określonym formacie.

*lpFormatEtc*<br/>
Wskazuje na strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym dane mają być oferowane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie poza formatem Schowka określonym przez *cfFormat*. Jeśli jest null, wartości domyślne są używane `FORMATETC` dla innych pól w strukturze.

### <a name="remarks"></a>Uwagi

Ta funkcja zapewnia dane przy użyciu natychmiastowego renderowania, więc należy podać dane podczas wywoływania funkcji; dane są buforowane, dopóki nie będzie to potrzebne. Użyj `CacheData` funkcji elementu członkowskiego, jeśli dostarczasz dużą ilość danych lub jeśli potrzebujesz ustrukturyzacyjnego nośnika pamięci.

Aby użyć opóźnionego [renderowania, należy wywołać delayRenderData](#delayrenderdata) lub [DelayRenderFileData funkcji członkowskiej.](#delayrenderfiledata) Aby uzyskać więcej informacji na temat opóźnionego renderowania obsługiwanego przez MFC, zobacz artykuł [Obiekty danych i źródła danych: Manipulacja](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [strukturę FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w sdk systemu Windows.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w windows SDK.

## <a name="coledatasourcecoledatasource"></a><a name="coledatasource"></a>Źródło COleDataSource::COleDataSource

Konstruuje `COleDataSource` obiekt.

```
COleDataSource();
```

## <a name="coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a>COleDataSource::DelayRenderData

Wywołanie tej funkcji, aby określić format, w którym dane są oferowane podczas operacji transferu danych.

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym dane mają być oferowane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwróconą przez natywną funkcję Windows [RegisterClipboardFormatat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Wskazuje na strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym dane mają być oferowane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie poza formatem Schowka określonym przez *cfFormat*. Jeśli jest null, wartości domyślne są używane `FORMATETC` dla innych pól w strukturze.

### <a name="remarks"></a>Uwagi

Ta funkcja zapewnia dane przy użyciu opóźnionego renderowania, więc dane nie są dostarczane natychmiast. [OnRenderData](#onrenderdata) lub [OnRenderGlobalData](#onrenderglobaldata) funkcji członkowskiej jest wywoływana do żądania danych.

Użyj tej funkcji, jeśli nie zamierzasz `CFile` podawać danych za pośrednictwem obiektu. Jeśli zamierzasz dostarczyć dane za `CFile` pośrednictwem obiektu, wywołaj [DelayRenderFileData](#delayrenderfiledata) funkcji członkowskiej. Aby uzyskać więcej informacji na temat opóźnionego renderowania obsługiwanego przez MFC, zobacz artykuł [Obiekty danych i źródła danych: Manipulacja](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby użyć natychmiastowego [renderowania, należy wywołać cachedata](#cachedata) lub [CacheGlobalData funkcji członkowskiej.](#cacheglobaldata)

Aby uzyskać więcej informacji, zobacz [strukturę FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w sdk systemu Windows.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w windows SDK.

## <a name="coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a>COleDataSource::DelayRenderFileData

Wywołanie tej funkcji, aby określić format, w którym dane są oferowane podczas operacji transferu danych.

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym dane mają być oferowane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwróconą przez natywną funkcję Windows [RegisterClipboardFormatat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Wskazuje na strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym dane mają być oferowane. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie poza formatem Schowka określonym przez *cfFormat*. Jeśli jest null, wartości domyślne są używane `FORMATETC` dla innych pól w strukturze.

### <a name="remarks"></a>Uwagi

Ta funkcja zapewnia dane przy użyciu opóźnionego renderowania, więc dane nie są dostarczane natychmiast. Funkcja elementu członkowskiego [OnRenderFileData](#onrenderfiledata) jest wywoływana do żądania danych.

Użyj tej funkcji, jeśli zamierzasz użyć `CFile` obiektu do dostarczania danych. Jeśli nie zamierzasz używać `CFile` obiektu, wywołaj [delayRenderData](#delayrenderdata) funkcji członkowskiej. Aby uzyskać więcej informacji na temat opóźnionego renderowania obsługiwanego przez MFC, zobacz artykuł [Obiekty danych i źródła danych: Manipulacja](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby użyć natychmiastowego [renderowania, należy wywołać cachedata](#cachedata) lub [CacheGlobalData funkcji członkowskiej.](#cacheglobaldata)

Aby uzyskać więcej informacji, zobacz [strukturę FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w sdk systemu Windows.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w windows SDK.

## <a name="coledatasourcedelaysetdata"></a><a name="delaysetdata"></a>COleDataSource::DelaySetData

Wywołanie tej funkcji do obsługi zmiany zawartości źródła danych.

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym mają być umieszczone dane. Ten parametr może być jednym ze wstępnie zdefiniowanych formatów Schowka lub wartością zwróconą przez natywną funkcję Windows [RegisterClipboardFormatat.](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) opisującą format, w którym dane mają być zastąpione. Podaj wartość tego parametru, jeśli chcesz określić dodatkowe informacje o formacie poza formatem Schowka określonym przez *cfFormat*. Jeśli jest null, wartości domyślne są używane `FORMATETC` dla innych pól w strukturze.

### <a name="remarks"></a>Uwagi

[OnSetData](#onsetdata) zostanie wywołana przez platformę, gdy tak się stanie. Jest to używane tylko wtedy, gdy struktura zwraca źródło danych z [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Jeśli `DelaySetData` nie zostanie `OnSetData` wywołana, funkcja nigdy nie zostanie wywołana. `DelaySetData`dla każdego obsługiwanego Schowka lub `FORMATETC` formatu.

Aby uzyskać więcej informacji, zobacz [strukturę FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) w sdk systemu Windows.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) w windows SDK.

## <a name="coledatasourcedodragdrop"></a><a name="dodragdrop"></a>COleDataSource::DoDragDrop

Wywołanie `DoDragDrop` funkcji elementu członkowskiego, aby wykonać operację przeciągania i upuszczania dla tego źródła danych, zazwyczaj w programie obsługi [CWnd::OnLButtonDown.](../../mfc/reference/cwnd-class.md#onlbuttondown)

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parametry

*dwEfektyty*<br/>
Operacje przeciągania i upuszczania, które są dozwolone w tym źródle danych. Może być co najmniej jedna z następujących czynności:

- DROPEFFECT_COPY Można wykonać operację kopiowania.

- DROPEFFECT_MOVE można wykonać operację przenoszenia.

- DROPEFFECT_LINK Można ustanowić łącze z usuniętych danych do oryginalnych danych.

- DROPEFFECT_SCROLL Wskazuje, że może wystąpić operacja przewijania przeciągania.

*lpRectStartDrag*<br/>
Wskaźnik do prostokąta, który definiuje, gdzie faktycznie rozpoczyna się przeciąganie. Aby uzyskać więcej informacji zobacz następujące sekcji uwag.

*PDropSource (źródło pDropSource)*<br/>
Wskazuje źródło upuszczania. Jeśli NULL następnie domyślna implementacja [COleDropSource](../../mfc/reference/coledropsource-class.md) będą używane.

### <a name="return-value"></a>Wartość zwracana

Efekt upuszczania generowany przez operację przeciągania i upuszczania; w przeciwnym razie DROPEFFECT_NONE, jeśli operacja nigdy nie rozpoczyna się, ponieważ użytkownik zwolnił przycisk myszy przed opuszczeniem dostarczonego prostokąta.

### <a name="remarks"></a>Uwagi

Operacja przeciągania i upuszczania nie rozpoczyna się natychmiast. Czeka, aż kursor myszy opuści prostokąt określony przez *lpRectStartDrag* lub do określonej liczby milisekund minęło. Jeśli *lpRectStartDrag* ma wartość NULL, rozmiar prostokąta wynosi jeden piksel.

Czas opóźnienia jest określony przez ustawienie klucza rejestru. Czas opóźnienia można zmienić, wywołując [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) lub [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Jeśli nie określisz czasu opóźnienia, używana jest wartość domyślna 200 milisekund. Czas opóźnienia przeciągania jest przechowywany w następujący sposób:

- Czas opóźnienia przeciągania systemu Windows NT jest przechowywany w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Czas opóźnienia przeciągania systemu Windows 3.x jest przechowywany w win. INI w sekcji [Windows}.

- Czas opóźnienia przeciągania systemu Windows 95/98 jest przechowywany w buforowanej wersji programu WIN. Ini.

Aby uzyskać więcej informacji o tym, jak informacje o opóźnieniu przeciągania są przechowywane w rejestrze lub pliku . INI, zobacz [WriteProfileString](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) w windows SDK.

Aby uzyskać więcej informacji, zobacz artykuł [OLE przeciąganie i upuszczanie](../../mfc/drag-and-drop-ole.md).

## <a name="coledatasourceempty"></a><a name="empty"></a>COleDataSource::Pusty

Wywołanie tej funkcji, aby opróżnić `COleDataSource` obiekt danych.

```
void Empty();
```

### <a name="remarks"></a>Uwagi

Formaty renderowania buforowane i opóźnione są opróżniane, dzięki czemu można je ponownie zużyć.

Aby uzyskać więcej informacji, zobacz [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) w windows SDK.

## <a name="coledatasourceflushclipboard"></a><a name="flushclipboard"></a>COleDataSource::FlushClipboard

Renderuje dane, które znajduje się w Schowku, a następnie umożliwia wklejenie danych ze Schowka po zamknięciu aplikacji.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Uwagi

Użyj [setclipboard,](#setclipboard) aby umieścić dane w Schowku.

## <a name="coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a>COleDataSource::GetClipboardOwner

Określa, czy dane w Schowku uległy zmianie od czasu ostatniego wywołania [SetClipboard,](#setclipboard) a jeśli tak, identyfikuje bieżącego właściciela.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Wartość zwracana

Źródło danych obecnie w Schowku lub NULL, jeśli w Schowku nie ma niczego lub jeśli Schowek nie jest własnością aplikacji wywołującej.

## <a name="coledatasourceonrenderdata"></a><a name="onrenderdata"></a>COleDataSource::OnRenderData

Wywoływane przez strukturę do pobierania danych w określonym formacie.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) określającą format, w którym wymagane są informacje.

*lpStgMedium*<br/>
Wskazuje strukturę [STGMEDIUM,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) w której dane mają być zwracane.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format to jeden wcześniej `COleDataSource` umieszczony w obiekcie przy użyciu [delayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) funkcji członkowskiej do opóźnionego renderowania. Domyślna implementacja tej funkcji wywoła [OnRenderFileData](#onrenderfiledata) lub [OnRenderGlobalData,](#onrenderglobaldata) jeśli dostarczony nośnik pamięci jest odpowiednio plikiem lub pamięcią. Jeśli żaden z tych formatów nie są dostarczane, a następnie domyślna implementacja zwróci 0 i nic nie robić. Aby uzyskać więcej informacji na temat opóźnionego renderowania obsługiwanego przez MFC, zobacz artykuł [Obiekty danych i źródła danych: Manipulacja](../../mfc/data-objects-and-data-sources-manipulation.md).

Jeśli *lpStgMedium*-> *tymed* jest TYMED_NULL, `STGMEDIUM` należy je przydzielić i wypełnić zgodnie z *lpFormatEtc->tymed*. Jeśli nie jest TYMED_NULL, `STGMEDIUM` należy wypełnić w miejscu z danymi.

Jest to zaawansowane zastąpienie. Zastąp tę funkcję, aby podać dane w żądanym formacie i nośniku. W zależności od danych można zastąpić jedną z innych wersji tej funkcji. Jeśli dane są małe i stałe, `OnRenderGlobalData`należy zastąpić . Jeśli dane są w pliku lub mają zmienny `OnRenderFileData`rozmiar, należy zastąpić .

Aby uzyskać więcej informacji, zobacz [struktury STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) i [FORMATETC,](/windows/win32/api/objidl/ns-objidl-formatetc) typ wyliczenia [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) i [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w windows SDK.

## <a name="coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a>COleDataSource::OnRenderFileData

Wywoływane przez strukturę do pobierania danych w określonym formacie, gdy określony nośnik pamięci jest plikiem.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) określającą format, w którym wymagane są informacje.

*p Plik*<br/>
Wskazuje obiekt [CFile,](../../mfc/reference/cfile-class.md) w którym mają być renderowane dane.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format to jeden wcześniej `COleDataSource` umieszczony w obiekcie przy użyciu [delayRenderData](#delayrenderdata) funkcji elementu członkowskiego do opóźnionego renderowania. Domyślna implementacja tej funkcji po prostu zwraca FALSE.

Jest to zaawansowane zastąpienie. Zastąp tę funkcję, aby podać dane w żądanym formacie i nośniku. W zależności od danych można zastąpić jedną z innych wersji tej funkcji. Jeśli chcesz obsłużyć wiele nośników pamięci masowej, należy zastąpić [onrenderdata](#onrenderdata). Jeśli dane są w pliku lub mają zmienny `OnRenderFileData`rozmiar, należy zastąpić . Aby uzyskać więcej informacji na temat opóźnionego renderowania obsługiwanego przez MFC, zobacz artykuł [Obiekty danych i źródła danych: Manipulacja](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [strukturę FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) i [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w usłudze Windows SDK.

## <a name="coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a>COleDataSource::OnRenderGlobalData

Wywoływana przez strukturę do pobierania danych w określonym formacie, gdy określonym nośnikiem pamięci jest pamięć globalna.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) określającą format, w którym wymagane są informacje.

*phGlobal (własówce)*<br/>
Wskazuje dojście do pamięci globalnej, w której mają być zwracane dane. Jeśli jeden nie został jeszcze przydzielony, ten parametr może być NULL.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Określony format to jeden wcześniej `COleDataSource` umieszczony w obiekcie przy użyciu [delayRenderData](#delayrenderdata) funkcji elementu członkowskiego do opóźnionego renderowania. Domyślna implementacja tej funkcji po prostu zwraca FALSE.

Jeśli *phGlobal* ma wartość NULL, nowy HGLOBAL powinien zostać przydzielony i zwrócony w *phGlobal*. W przeciwnym razie HGLOBAL określony przez *phGlobal* powinien być wypełniony danymi. Ilość danych umieszczonych w HGLOBAL nie może przekraczać bieżącego rozmiaru bloku pamięci. Ponadto bloku nie można ponownie przydzielić do większego rozmiaru.

Jest to zaawansowane zastąpienie. Zastąp tę funkcję, aby podać dane w żądanym formacie i nośniku. W zależności od danych można zastąpić jedną z innych wersji tej funkcji. Jeśli chcesz obsłużyć wiele nośników pamięci masowej, należy zastąpić [onrenderdata](#onrenderdata). Jeśli dane są w pliku lub mają zmienny rozmiar, należy zastąpić [onrenderfiledata](#onrenderfiledata). Aby uzyskać więcej informacji na temat opóźnionego renderowania obsługiwanego przez MFC, zobacz artykuł [Obiekty danych i źródła danych: Manipulacja](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [strukturę FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) i [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w usłudze Windows SDK.

## <a name="coledatasourceonsetdata"></a><a name="onsetdata"></a>COleDataSource::OnSetData

Wywoływane przez strukturę, aby ustawić `COleDataSource` lub zastąpić dane w obiekcie w określonym formacie.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje strukturę [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) określającą format, w którym dane są zastępowane.

*lpStgMedium*<br/>
Wskazuje strukturę [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) zawierającą dane, które zastąpią `COleDataSource` bieżącą zawartość obiektu.

*Brelease*<br/>
Wskazuje, kto jest właścicielem nośnika danych po zakończeniu wywołania funkcji. Osoba wywołująca decyduje, kto jest odpowiedzialny za zwolnienie zasobów przydzielonych w imieniu nośnika danych. Wywołujący robi to, ustawiając *bWyzwaj*. Jeśli *bWyzwanie* jest niezerowe, źródło danych przejmuje na własność, zwalniając nośnik po zakończeniu używania go. Gdy *bWydaj* jest 0, obiekt wywołujący zachowuje własność i źródło danych można użyć nośnika magazynu tylko na czas trwania wywołania.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Źródło danych nie przejmie na własność danych, dopóki nie pomyślnie je uzyskało. Oznacza to, że nie `OnSetData` bierze na siebie, jeśli zwraca 0. Jeśli źródło danych przejmuje na własność, zwalnia nośnik pamięci masowej, wywołując [funkcję ReleaseStgMedium.](/windows/win32/api/ole2/nf-ole2-releasestgmedium)

Domyślna implementacja nic nie robi. Zastąp tę funkcję, aby zastąpić dane w określonym formacie. Jest to zaawansowane zastąpienie.

Aby uzyskać więcej informacji, zobacz [struktury STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) i [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) oraz [funkcje ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) i [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) w windows SDK.

## <a name="coledatasourcesetclipboard"></a><a name="setclipboard"></a>COleDataSource::SetClipboard

Umieszcza dane zawarte w `COleDataSource` obiekcie w Schowku po wywołaniu jednej z następujących funkcji: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata)lub [DelayRenderFileData](#delayrenderfiledata).

```
void SetClipboard();
```

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Próbka MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDataObject](../../mfc/reference/coledataobject-class.md)
