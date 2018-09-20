---
title: Klasa COleDataSource | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2aa5ea0b95235d778c6491cca5eeb6b4a826b8bd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428112"
---
# <a name="coledatasource-class"></a>Klasa COleDataSource

Działa jako bufor, w której aplikacja umieszcza dane, które będzie oferować podczas danych transferu operacji, takich jak Schowek lub operacji przeciągania i upuszczania.

## <a name="syntax"></a>Składnia

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDataSource::COleDataSource](#coledatasource)|Konstruuje `COleDataSource` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleDataSource::CacheData](#cachedata)|Udostępnia dane w określonym formacie przy użyciu `STGMEDIUM` struktury.|
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Udostępnia dane w określonym formacie przy użyciu wartości HGLOBAL.|
|[COleDataSource::DelayRenderData](#delayrenderdata)|Udostępnia dane w określonym formacie za pomocą opóźnione renderowanie.|
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Udostępnia dane w określonym formacie w `CFile` wskaźnika.|
|[COleDataSource::DelaySetData](#delaysetdata)|Wywoływana dla każdego formatu, który jest obsługiwany w `OnSetData`.|
|[COleDataSource::DoDragDrop](#dodragdrop)|Wykonuje operacje przeciągania i upuszczania ze źródłem danych.|
|[COleDataSource::Empty](#empty)|Opróżnia `COleDataSource` obiektu danych.|
|[COleDataSource::FlushClipboard](#flushclipboard)|Wyświetla wszystkie dane do Schowka.|
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Weryfikuje, czy dane w Schowku znajduje nadal istnieje.|
|[COleDataSource::OnRenderData](#onrenderdata)|Pobiera dane jako część opóźnione renderowanie.|
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Pobiera dane do `CFile` jako część opóźnione renderowanie.|
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Pobiera dane do wartości HGLOBAL jako część opóźnione renderowanie.|
|[COleDataSource::OnSetData](#onsetdata)|Wywołuje się, by podmienić dane w `COleDataSource` obiektu.|
|[COleDataSource::SetClipboard](#setclipboard)|Umieszcza `COleDataSource` obiektu do Schowka.|

## <a name="remarks"></a>Uwagi

Można utworzyć źródła danych OLE bezpośrednio. Alternatywnie [COleClientItem](../../mfc/reference/coleclientitem-class.md) i [COleServerItem](../../mfc/reference/coleserveritem-class.md) klasy tworzenia źródeł danych OLE w odpowiedzi na swoje `CopyToClipboard` i `DoDragDrop` funkcji elementów członkowskich. Zobacz [COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) krótki opis. Zastąp `OnGetClipboardData` funkcji składowej klasy klienta element lub serwera elementu Dodawanie dodatkowych formaty Schowka do danych ze źródła danych OLE są tworzone dla `CopyToClipboard` lub `DoDragDrop` funkcja elementu członkowskiego.

Zawsze, gdy chcesz przygotować dane transferu, należy utworzyć obiekt tej klasy i wypełnić ją z danymi przy użyciu metody najbardziej odpowiednie dla Twoich danych. Ten sposób jest wstawiany do źródła danych bezpośrednio jest zależna od tego, czy dane są dostarczane bezpośrednio (natychmiastowego renderowania) lub na żądanie (opóźnione renderowanie). Dla każdego format Schowka są dostarczania danych, przekazując format schowka do użycia (i opcjonalnie [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury), wywołaj [DelayRenderData](#delayrenderdata).

Aby uzyskać więcej informacji na temat źródeł danych i transfer danych, zobacz artykuł [obiekty danych i źródeł danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Ponadto, artykuł [tematy Schowka](../../mfc/clipboard.md) opisuje z mechanizmu Schowka OLE.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="cachedata"></a>  COleDataSource::CacheData

Wywołaj tę funkcję, aby określić format, w którym dane są oferowane w trakcie danych operacji transferu.

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym ma być oferowane danych. Ten parametr może być jednym z wstępnie zdefiniowane formaty Schowka lub wartość zwrócona przez obiekt natywny Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji.

*lpStgMedium*<br/>
Wskazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) zawierające dane w formacie określonym struktury.

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) opisujący format, w której dane mają być oferowane struktury. Podaj wartość dla tego parametru, jeśli chcesz określić informacji o formacie dodatkowe poza określonym przez format schowka *cfFormat*. Jeśli ma wartość NULL, wartości domyślne są używane dla innych pól w `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

Należy podać dane, ponieważ ta funkcja udostępnia je za pomocą natychmiastowej renderowania. Dane są buforowane, dopóki nie jest wymagane.

Podaj dane za pomocą [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury. Można również użyć `CacheGlobalData` funkcja elementu członkowskiego, jeśli dostarczenie ilość danych jest wystarczająco mała, należy dokonać wydajnie za pomocą wartości HGLOBAL.

Po wywołaniu `CacheData` `ptd` członkiem `lpFormatEtc` i zawartość *lpStgMedium* należą do obiektu danych, nie przez obiekt wywołujący.

Aby użyć opóźnione renderowanie, należy wywołać [DelayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsłużony przez MFC, zobacz artykuł [obiekty danych i źródeł danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) i [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktur w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w zestawie Windows SDK.

##  <a name="cacheglobaldata"></a>  COleDataSource::CacheGlobalData

Wywołaj tę funkcję, aby określić format, w którym dane są oferowane w trakcie danych operacji transferu.

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym ma być oferowane danych. Ten parametr może być jednym z wstępnie zdefiniowane formaty Schowka lub wartość zwrócona przez obiekt natywny Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji.

*wartości hGlobal*<br/>
Dojście do bloku pamięci globalnej, zawierające dane w formacie określonym.

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) opisujący format, w której dane mają być oferowane struktury. Podaj wartość dla tego parametru, jeśli chcesz określić informacji o formacie dodatkowe poza określonym przez format schowka *cfFormat*. Jeśli ma wartość NULL, wartości domyślne są używane dla innych pól w `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

Ta funkcja udostępnia dane za pomocą natychmiastowej renderowania, dzięki czemu dane należy podać podczas wywoływania funkcji; dane są buforowane, dopóki nie jest wymagane. Użyj `CacheData` funkcja elementu członkowskiego, jeśli są podawania dużej ilości danych lub jeśli potrzebujesz nośnika magazynowania ze strukturą.

Aby użyć opóźnione renderowanie, należy wywołać [DelayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsłużony przez MFC, zobacz artykuł [obiekty danych i źródeł danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w zestawie Windows SDK.

##  <a name="coledatasource"></a>  COleDataSource::COleDataSource

Konstruuje `COleDataSource` obiektu.

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>  COleDataSource::DelayRenderData

Wywołaj tę funkcję, aby określić format, w którym dane są oferowane w trakcie danych operacji transferu.

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym ma być oferowane danych. Ten parametr może być jednym z wstępnie zdefiniowane formaty Schowka lub wartość zwrócona przez obiekt natywny Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji.

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) opisujący format, w której dane mają być oferowane struktury. Podaj wartość dla tego parametru, jeśli chcesz określić informacji o formacie dodatkowe poza określonym przez format schowka *cfFormat*. Jeśli ma wartość NULL, wartości domyślne są używane dla innych pól w `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

Ta funkcja udostępnia dane za pomocą opóźnione renderowanie, dzięki czemu dane nie są dostarczane bezpośrednio. [OnRenderData](#onrenderdata) lub [OnRenderGlobalData](#onrenderglobaldata) funkcja członkowska jest wywoływana w celu żądania danych.

Użyj tej funkcji, jeśli nie chcesz podać dane za pomocą `CFile` obiektu. Jeśli źródło danych za pośrednictwem `CFile` obiektu, wywołaj [DelayRenderFileData](#delayrenderfiledata) funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsłużony przez MFC, zobacz artykuł [obiekty danych i źródeł danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Umożliwia renderowanie bezpośredniego, należy wywołać [CacheData](#cachedata) lub [CacheGlobalData](#cacheglobaldata) funkcja elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w zestawie Windows SDK.

##  <a name="delayrenderfiledata"></a>  COleDataSource::DelayRenderFileData

Wywołaj tę funkcję, aby określić format, w którym dane są oferowane w trakcie danych operacji transferu.

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym ma być oferowane danych. Ten parametr może być jednym z wstępnie zdefiniowane formaty Schowka lub wartość zwrócona przez obiekt natywny Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji.

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) opisujący format, w której dane mają być oferowane struktury. Podaj wartość dla tego parametru, jeśli chcesz określić informacji o formacie dodatkowe poza określonym przez format schowka *cfFormat*. Jeśli ma wartość NULL, wartości domyślne są używane dla innych pól w `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

Ta funkcja udostępnia dane za pomocą opóźnione renderowanie, dzięki czemu dane nie są dostarczane bezpośrednio. [OnRenderFileData](#onrenderfiledata) funkcja członkowska jest wywoływana w celu żądania danych.

Użyj tej funkcji, jeśli zamierzasz używać `CFile` obiektu jako źródło danych. Jeśli nie zamierzasz używać `CFile` obiektu, wywołaj [DelayRenderData](#delayrenderdata) funkcja elementu członkowskiego. Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsłużony przez MFC, zobacz artykuł [obiekty danych i źródeł danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Umożliwia renderowanie bezpośredniego, należy wywołać [CacheData](#cachedata) lub [CacheGlobalData](#cacheglobaldata) funkcja elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w zestawie Windows SDK.

##  <a name="delaysetdata"></a>  COleDataSource::DelaySetData

Wywołaj tę funkcję, aby obsługiwać zmiany zawartości źródła danych.

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parametry

*cfFormat*<br/>
Format Schowka, w którym ma być przełączony danych. Ten parametr może być jednym z wstępnie zdefiniowane formaty Schowka lub wartość zwrócona przez obiekt natywny Windows [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) funkcji.

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury opisujący format danych ma zostać zastąpiony. Podaj wartość dla tego parametru, jeśli chcesz określić informacji o formacie dodatkowe poza określonym przez format schowka *cfFormat*. Jeśli ma wartość NULL, wartości domyślne są używane dla innych pól w `FORMATETC` struktury.

### <a name="remarks"></a>Uwagi

[OnSetData](#onsetdata) wywoływane przez platformę w takiej sytuacji. Jest ona używana tylko, gdy struktura zwraca źródła danych z [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Jeśli `DelaySetData` nie jest wywoływana z `OnSetData` funkcja nigdy nie zostanie wywołana. `DelaySetData` powinna być wywoływana dla każdego Schowka lub `FORMATETC` formatu, które obsługujesz.

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](/windows/desktop/api/winuser/nf-winuser-registerclipboardformata) w zestawie Windows SDK.

##  <a name="dodragdrop"></a>  COleDataSource::DoDragDrop

Wywołaj `DoDragDrop` funkcja elementu członkowskiego do wykonywania operacji przeciągania i upuszczania dla tego źródła danych, zazwyczaj w [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) programu obsługi.

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>Parametry

*dwEffects*<br/>
Przeciągnij i upuść operacje, które są dozwolone w tym źródle danych. Może być co najmniej jeden z następujących czynności:

- DROPEFFECT_COPY, które można wykonać operacji kopiowania.

- DROPEFFECT_MOVE, które można wykonać operacji przenoszenia.

- Można było ustalić DROPEFFECT_LINK link pocztą e-mail od elementów usuniętych danych oryginalnych danych.

- DROPEFFECT_SCROLL wskazuje, że operacji przeciągania przewijania mogą wystąpić.

*lpRectStartDrag*<br/>
Wskaźnik do prostokąt, który definiuje, w którym faktycznie zacznie przeciągania. Aby uzyskać więcej informacji zobacz następujące sekcji uwag.

*pDropSource*<br/>
Wskazuje źródło porzucenia. Jeśli wartość NULL, następnie domyślną implementację elementu [COleDropSource](../../mfc/reference/coledropsource-class.md) będą używane.

### <a name="return-value"></a>Wartość zwracana

Efekt generowane przez operację przeciągania i upuszczania; w przeciwnym razie DROPEFFECT_NONE Jeśli nigdy nie rozpocznie się wykonywanie operacji, ponieważ użytkownik wydane przycisku myszy przed opuszczeniem podany prostokąt.

### <a name="remarks"></a>Uwagi

Operacja przeciągania i upuszczania nie rozpoczyna się natychmiast. Czeka, aż kursor myszy opuszcza prostokąt określony przez *lpRectStartDrag* lub dopóki nie przeszły przez określoną liczbę milisekund. Jeśli *lpRectStartDrag* ma wartość NULL, rozmiar prostokąta wynosi jeden piksel.

Czas opóźnienia jest określona przez ustawienie klucza rejestru. Możesz zmienić czas opóźnienia, wywołując [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) lub [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Jeśli nie określisz czas opóźnienia, jest używana domyślna wartość 200 ms. Przeciągnij opóźnienia są przechowywane w następujący sposób:

- Czas opóźnienia przeciągania Windows NT jest przechowywany w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.

- Czas opóźnienia przeciągania 3.x Windows są przechowywane w ZWYCIĘSTWA. Plik INI, w sekcji [Windows}.

- Przeciągnij Windows 95/98 opóźnienia są przechowywane w pamięci podręcznej wersji systemu Windows. PLIKU INI.

Dla przeciągnij więcej informacji o tym, jak opóźnienie informacje są przechowywane w rejestrze albo lub. Plik INI, zobacz [WriteProfileString](/windows/desktop/api/winbase/nf-winbase-writeprofilestringa) w zestawie Windows SDK.

Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie źródłowego porzucić](../../mfc/drag-and-drop-implementing-a-drop-source.md).

##  <a name="empty"></a>  COleDataSource::Empty

Wywołaj tę funkcję na pusty `COleDataSource` obiektu danych.

```
void Empty();
```

### <a name="remarks"></a>Uwagi

Zarówno w pamięci podręcznej i formatów renderowania opóźnienia są opróżnienia, dzięki czemu mogą być ponownie używane.

Aby uzyskać więcej informacji, zobacz [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) w zestawie Windows SDK.

##  <a name="flushclipboard"></a>  COleDataSource::FlushClipboard

Renderuje dane do Schowka, a następnie umożliwia wklejenie danych ze Schowka, po zamknięciu aplikacji.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>Uwagi

Użyj [Funkcja SetClipboard](#setclipboard) umieszczanie danych w Schowku.

##  <a name="getclipboardowner"></a>  COleDataSource::GetClipboardOwner

Określa, czy dane w Schowku zmienił się od [Funkcja SetClipboard](#setclipboard) ostatnio została wywołana i jeśli tak, określa bieżący właściciel.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>Wartość zwracana

Dane źródła aktualnie w Schowku lub wartość NULL, jeśli nie ma nic w Schowku lub Schowka nie jest własnością aplikacji wywołującej.

##  <a name="onrenderdata"></a>  COleDataSource::OnRenderData

Metoda wywoływana przez platformę, by pobrać dane w określonym formacie.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Struktura określająca format, w którym wymagane informacje.

*lpStgMedium*<br/>
Wskazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury, w którym ma zostać zwrócone dane.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podany format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) funkcję członkowską opóźnione renderowanie. Domyślna implementacja tej funkcji będzie wywoływać [OnRenderFileData](#onrenderfiledata) lub [OnRenderGlobalData](#onrenderglobaldata) przypadku nośnik dostarczony plik lub pamięć, odpowiednio. Jeśli żadna z tych formatów jest podany, domyślna implementacja będzie zwracają 0 i nic nie rób. Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsłużony przez MFC, zobacz artykuł [obiekty danych i źródeł danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Jeśli *lpStgMedium*-> *tymed* jest TYMED_NULL, `STGMEDIUM` powinny być przydzielny i wypełnione określony przez *lpFormatEtc -> tymed*. Jeśli nie jest TYMED_NULL, `STGMEDIUM` powinno być wypełnione w miejscu z danymi.

Jest to zaawansowany możliwym do zastąpienia. Zastąp tę funkcję, aby podać dane w żądany format i średnia. W zależności od danych można zastąpić jedną z innych wersji tej funkcji, zamiast tego. W przypadku małych i stały rozmiar danych zastąpić `OnRenderGlobalData`. Jeśli Twoje dane znajduje się w pliku, lub o zmiennym rozmiarze, zastąpić `OnRenderFileData`.

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) i [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktur, [TYMED](/windows/desktop/api/objidl/ne-objidl-tagtymed) typ wyliczeniowy i [Metoda IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) w Windows SDK.

##  <a name="onrenderfiledata"></a>  COleDataSource::OnRenderFileData

Metoda wywoływana przez platformę, by pobrać dane w określonym formacie po nośnika magazynowania określonego pliku.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Struktura określająca format, w którym wymagane informacje.

*pFile*<br/>
Wskazuje [CFile](../../mfc/reference/cfile-class.md) obiekt danych ma być renderowany.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podany format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](#delayrenderdata) funkcję członkowską opóźnione renderowanie. Domyślna implementacja tej funkcji, po prostu zwraca wartość FALSE.

Jest to zaawansowany możliwym do zastąpienia. Zastąp tę funkcję, aby podać dane w żądany format i średnia. W zależności od danych można zastąpić jedną z innych wersji tej funkcji, zamiast tego. Jeśli chcesz obsługiwać wiele nośników, zastępują [OnRenderData](#onrenderdata). Jeśli Twoje dane znajduje się w pliku, lub o zmiennym rozmiarze, zastąpić `OnRenderFileData`. Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsłużony przez MFC, zobacz artykuł [obiekty danych i źródeł danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury i [Metoda IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) w zestawie Windows SDK.

##  <a name="onrenderglobaldata"></a>  COleDataSource::OnRenderGlobalData

Metoda wywoływana przez platformę, by pobrać dane w określonym formacie po określonym nośniku pamięci globalnej.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) Struktura określająca format, w którym wymagane informacje.

*phGlobal*<br/>
Wskazuje dojścia do pamięci globalnej, w którym ma zostać zwrócone dane. Jeśli jeden nie jeszcze przydzielone, ten parametr może być równa NULL.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Podany format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](#delayrenderdata) funkcję członkowską opóźnione renderowanie. Domyślna implementacja tej funkcji, po prostu zwraca wartość FALSE.

Jeśli *phGlobal* ma wartość NULL, a następnie nowe wartości HGLOBAL powinien być przydzielony i zwracane w *phGlobal*. W przeciwnym razie wartości HGLOBAL określony przez *phGlobal* powinno być wypełnione przy użyciu danych. Ilość danych, umieszczone w wartości HGLOBAL nie może przekraczać bieżący rozmiar bloku pamięci. Ponadto nie można ponownie przydzielane bloku, na większy rozmiar.

Jest to zaawansowany możliwym do zastąpienia. Zastąp tę funkcję, aby podać dane w żądany format i średnia. W zależności od danych można zastąpić jedną z innych wersji tej funkcji, zamiast tego. Jeśli chcesz obsługiwać wiele nośników, zastępują [OnRenderData](#onrenderdata). Jeśli Twoje dane znajduje się w pliku, lub o zmiennym rozmiarze, zastąpić [OnRenderFileData](#onrenderfiledata). Aby uzyskać więcej informacji na temat opóźnionego renderowania jako obsłużony przez MFC, zobacz artykuł [obiekty danych i źródeł danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).

Aby uzyskać więcej informacji, zobacz [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury i [Metoda IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) w zestawie Windows SDK.

##  <a name="onsetdata"></a>  COleDataSource::OnSetData

Wywoływane przez platformę, by ustawić lub podmienić dane w `COleDataSource` obiektu w określonym formacie.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>Parametry

*lpFormatEtc*<br/>
Wskazuje [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury, określając format, w którym dane są zastępowane.

*lpStgMedium*<br/>
Wskazuje [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) struktury zawierającej dane, które zastąpi bieżącą zawartość `COleDataSource` obiektu.

*bRelease*<br/>
Wskazuje, kto jest właścicielem nośnika magazynowania po wykonaniu wywołania funkcji. Obiekt wywołujący decyduje o tym, kto jest odpowiedzialny za przy zwalnianiu zasobów przydzielonych w imieniu nośnika magazynowania. Obiekt wywołujący robi to poprzez ustawienie *bRelease*. Jeśli *bRelease* jest różna od zera, źródła danych przejmuje, zwalniając nośnik, po zakończeniu korzystania z niego. Gdy *bRelease* jest 0, obiekt wywołujący zachowuje własność i źródła danych przy użyciu nośnika magazynowania tylko na czas trwania wywołania.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Źródło danych dopiero właściciela danych został pomyślnie uzyskał go. Oznacza to, go nie przejęcie na własność Jeśli `OnSetData` zwraca wartość 0. Jeśli źródło danych przejmuje na własność, zwalnia nośnika magazynowania, wywołując [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) funkcji.

Domyślna implementacja nic nie robi. Należy przesłonić tę funkcję, aby zamienić dane w określonym formacie. Jest to zaawansowany możliwym do zastąpienia.

Aby uzyskać więcej informacji, zobacz [STGMEDIUM](/windows/desktop/api/objidl/ns-objidl-tagstgmedium) i [FORMATETC](/windows/desktop/api/objidl/ns-objidl-tagformatetc) struktury i [ReleaseStgMedium](/windows/desktop/api/ole2/nf-ole2-releasestgmedium) i [Metoda IDataObject::GetData](/windows/desktop/api/objidl/nf-objidl-idataobject-getdata) Funkcje zestawu Windows SDK.

##  <a name="setclipboard"></a>  COleDataSource::SetClipboard

Umieszcza dane zawarte w `COleDataSource` obiektu w Schowku po wywołaniu jednej z następujących funkcji: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata), lub [DelayRenderFileData](#delayrenderfiledata).

```
void SetClipboard();
```

## <a name="see-also"></a>Zobacz też

[Próbki MFC HIERSVR](../../visual-cpp-samples.md)<br/>
[Próbki MFC OCLIENT](../../visual-cpp-samples.md)<br/>
[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleDataObject](../../mfc/reference/coledataobject-class.md)
