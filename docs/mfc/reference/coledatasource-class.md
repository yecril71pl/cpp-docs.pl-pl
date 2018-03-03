---
title: Klasa COleDataSource | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ce9abdccba549e0b0fd3c55bfb7fbaee6a11e27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coledatasource-class"></a>COleDataSource — klasa
Działa jako pamięci podręcznej, w którym aplikacja umieszcza dane, które będzie oferować podczas danych transfer operacji, takich jak Schowek lub operacji przeciągania i upuszczania.  
  
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
|[COleDataSource::CacheData](#cachedata)|Oferuje dane w określonym formacie przy użyciu **STGMEDIUM** struktury.|  
|[COleDataSource::CacheGlobalData](#cacheglobaldata)|Oferuje dane w określonym formacie przy użyciu `HGLOBAL`.|  
|[COleDataSource::DelayRenderData](#delayrenderdata)|Udostępnia dane w formacie określonym przy użyciu opóźnionego renderowania.|  
|[COleDataSource::DelayRenderFileData](#delayrenderfiledata)|Oferuje dane w formacie określonym w `CFile` wskaźnika.|  
|[COleDataSource::DelaySetData](#delaysetdata)|Wywołuje się, co formatu, który jest obsługiwany przez `OnSetData`.|  
|[COleDataSource::DoDragDrop](#dodragdrop)|Wykonuje operacje przeciągania i upuszczania ze źródłem danych.|  
|[COleDataSource::Empty](#empty)|Opróżnia `COleDataSource` obiektu danych.|  
|[COleDataSource::FlushClipboard](#flushclipboard)|Wyświetla wszystkie dane do Schowka.|  
|[COleDataSource::GetClipboardOwner](#getclipboardowner)|Weryfikuje, czy dane w Schowku znajduje nadal istnieje.|  
|[COleDataSource::OnRenderData](#onrenderdata)|Pobiera dane jako część opóźnione renderowanie.|  
|[COleDataSource::OnRenderFileData](#onrenderfiledata)|Pobiera dane do `CFile` jako część opóźnione renderowanie.|  
|[COleDataSource::OnRenderGlobalData](#onrenderglobaldata)|Pobiera dane do `HGLOBAL` jako część opóźnione renderowanie.|  
|[COleDataSource::OnSetData](#onsetdata)|Wywołuje się, aby zamienić dane w `COleDataSource` obiektu.|  
|[COleDataSource::SetClipboard](#setclipboard)|Miejsca `COleDataSource` obiektu w Schowku.|  
  
## <a name="remarks"></a>Uwagi  
 Można utworzyć źródła danych OLE bezpośrednio. Alternatywnie [COleClientItem](../../mfc/reference/coleclientitem-class.md) i [COleServerItem](../../mfc/reference/coleserveritem-class.md) klasy tworzenia źródła danych OLE w odpowiedzi na ich `CopyToClipboard` i `DoDragDrop` funkcji elementów członkowskich. Zobacz [COleServerItem::CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) krótki opis. Zastąpienie `OnGetClipboardData` funkcji członkowskiej klasy elementu lub serwer elementu Klasa klienta można dodać dodatkowe formaty Schowka do danych w źródle danych, OLE utworzone dla `CopyToClipboard` lub `DoDragDrop` funkcję elementu członkowskiego.  
  
 Zawsze, gdy chcesz przygotować transferu danych, należy utworzyć obiekt tej klasy i uzupełnij go z danymi przy użyciu metody najbardziej odpowiednie dla danych. Sposób dodaje się do źródła danych bezpośrednio dotyczy tego, czy dane są dostarczane bezpośrednio (natychmiastowe renderowania) lub na żądanie (opóźnione renderowanie). Dla każdego formatu Schowka, w którym udostępniasz dane przez przekazanie formatu Schowka do użycia (i opcjonalnie [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury), wywołaj [DelayRenderData](#delayrenderdata).  
  
 Aby uzyskać więcej informacji na temat źródeł danych i transferu danych, zobacz artykuł [obiekty danych i źródła danych (OLE)](../../mfc/data-objects-and-data-sources-ole.md). Ponadto artykuł [tematy Schowka](../../mfc/clipboard.md) opisuje z mechanizmu Schowka OLE.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleDataSource`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="cachedata"></a>COleDataSource::CacheData  
 Wywołanie tej funkcji, aby określić format, w którym danych jest oferowany podczas danych operacji transferu.  
  
```  
void CacheData(
    CLIPFORMAT cfFormat,  
    LPSTGMEDIUM lpStgMedium,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Format Schowka, w którym ma być oferowana danych. Ten parametr może być jedną z wstępnie zdefiniowane formaty Schowka lub wartość zwracana przez natywnego Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkcji.  
  
 `lpStgMedium`  
 Wskazuje [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury zawierającej dane w formacie określonym.  
  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury opisujące format, w którym ma być oferowana danych. Podaj wartość dla tego parametru, jeśli chcesz określić format dodatkowych informacji poza określonej przez format schowka `cfFormat`. Jeśli jest **NULL**, zostaną użyte wartości domyślne dla innych pól **FORMATETC** struktury.  
  
### <a name="remarks"></a>Uwagi  
 Należy podać danych, ponieważ ta funkcja udostępnia go za pomocą bezpośredniego renderowania. Dane są buforowane, dopóki nie potrzebne.  
  
 Podaj danych przy użyciu [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury. Można również użyć `CacheGlobalData` funkcji członkowskiej, jeśli ilość danych, podając jest duże, aby dokonać transferu efektywne wykorzystanie `HGLOBAL`.  
  
 Po wywołaniu `CacheData` **ptd** członkiem `lpFormatEtc` i zawartość `lpStgMedium` właścicielem jest obiekt danych nie przez obiekt wywołujący.  
  
 Do korzystania z renderowania opóźnione, wywołaj [DelayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) funkcję elementu członkowskiego. Aby uzyskać więcej informacji na opóźnione renderowanie, ponieważ obsługiwane przez MFC, zobacz artykuł [obiekty danych i źródła danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Aby uzyskać więcej informacji, zobacz [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) i [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w zestawie Windows SDK.  
  
##  <a name="cacheglobaldata"></a>COleDataSource::CacheGlobalData  
 Wywołanie tej funkcji, aby określić format, w którym danych jest oferowany podczas danych operacji transferu.  
  
```  
void CacheGlobalData(
    CLIPFORMAT cfFormat,  
    HGLOBAL hGlobal,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Format Schowka, w którym ma być oferowana danych. Ten parametr może być jedną z wstępnie zdefiniowane formaty Schowka lub wartość zwracana przez natywnego Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkcji.  
  
 *wartości hGlobal*  
 Dojście do bloku pamięci globalnej zawierające dane w formacie określonym.  
  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury opisujące format, w którym ma być oferowana danych. Podaj wartość dla tego parametru, jeśli chcesz określić format dodatkowych informacji poza określonej przez format schowka `cfFormat`. Jeśli jest **NULL**, zostaną użyte wartości domyślne dla innych pól **FORMATETC** struktury.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja udostępnia dane przy użyciu renderowania bezpośredniego, należy podać danych podczas wywoływania funkcji; dane są buforowane, dopóki nie potrzebne. Użyj `CacheData` funkcji członkowskiej, jeśli są dostarczanie dużej ilości danych lub jeśli wymagają średniej lub magazynem strukturalnym.  
  
 Do korzystania z renderowania opóźnione, wywołaj [DelayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) funkcję elementu członkowskiego. Aby uzyskać więcej informacji na opóźnione renderowanie, ponieważ obsługiwane przez MFC, zobacz artykuł [obiekty danych i źródła danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Aby uzyskać więcej informacji, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w zestawie Windows SDK.  
  
##  <a name="coledatasource"></a>COleDataSource::COleDataSource  
 Konstruuje `COleDataSource` obiektu.  
  
```  
COleDataSource();
```  
  
##  <a name="delayrenderdata"></a>COleDataSource::DelayRenderData  
 Wywołanie tej funkcji, aby określić format, w którym danych jest oferowany podczas danych operacji transferu.  
  
```  
void DelayRenderData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Format Schowka, w którym ma być oferowana danych. Ten parametr może być jedną z wstępnie zdefiniowane formaty Schowka lub wartość zwracana przez natywnego Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkcji.  
  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury opisujące format, w którym ma być oferowana danych. Podaj wartość dla tego parametru, jeśli chcesz określić format dodatkowych informacji poza określonej przez format schowka `cfFormat`. Jeśli jest **NULL**, zostaną użyte wartości domyślne dla innych pól **FORMATETC** struktury.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja udostępnia dane przy użyciu renderowania opóźnione, więc dane nie są dostarczane bezpośrednio. [OnRenderData](#onrenderdata) lub [OnRenderGlobalData](#onrenderglobaldata) funkcja członkowska jest wywoływana w celu żądania danych.  
  
 Użyj tej funkcji, jeśli nie zamierzasz dostarczyć danych przy użyciu `CFile` obiektu. Jeśli zamierzasz dostarczyć danych za pośrednictwem `CFile` obiekt, należy wywołać [DelayRenderFileData](#delayrenderfiledata) funkcję elementu członkowskiego. Aby uzyskać więcej informacji na opóźnione renderowanie, ponieważ obsługiwane przez MFC, zobacz artykuł [obiekty danych i źródła danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Do korzystania z renderowania bezpośredniego, należy wywołać [CacheData](#cachedata) lub [CacheGlobalData](#cacheglobaldata) funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w zestawie Windows SDK.  
  
##  <a name="delayrenderfiledata"></a>COleDataSource::DelayRenderFileData  
 Wywołanie tej funkcji, aby określić format, w którym danych jest oferowany podczas danych operacji transferu.  
  
```  
void DelayRenderFileData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Format Schowka, w którym ma być oferowana danych. Ten parametr może być jedną z wstępnie zdefiniowane formaty Schowka lub wartość zwracana przez natywnego Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkcji.  
  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury opisujące format, w którym ma być oferowana danych. Podaj wartość dla tego parametru, jeśli chcesz określić format dodatkowych informacji poza określonej przez format schowka `cfFormat`. Jeśli jest **NULL**, zostaną użyte wartości domyślne dla innych pól **FORMATETC** struktury.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja udostępnia dane przy użyciu renderowania opóźnione, więc dane nie są dostarczane bezpośrednio. [OnRenderFileData](#onrenderfiledata) funkcja członkowska jest wywoływana w celu żądania danych.  
  
 Użyj tej funkcji, jeśli zamierzasz używać `CFile` obiektu jako źródło danych. Jeśli nie zamierzasz używać `CFile` obiekt, należy wywołać [DelayRenderData](#delayrenderdata) funkcję elementu członkowskiego. Aby uzyskać więcej informacji na opóźnione renderowanie, ponieważ obsługiwane przez MFC, zobacz artykuł [obiekty danych i źródła danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Do korzystania z renderowania bezpośredniego, należy wywołać [CacheData](#cachedata) lub [CacheGlobalData](#cacheglobaldata) funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w zestawie Windows SDK.  
  
##  <a name="delaysetdata"></a>COleDataSource::DelaySetData  
 Wywołanie tej funkcji do obsługi zmiany zawartości ze źródłem danych.  
  
```  
void DelaySetData(
    CLIPFORMAT cfFormat,  
    LPFORMATETC lpFormatEtc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `cfFormat`  
 Format Schowka, w którym ma być umieszczone dane. Ten parametr może być jedną z wstępnie zdefiniowane formaty Schowka lub wartość zwracana przez natywnego Windows [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funkcji.  
  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury opisujące format, w którym ma zostać zastąpiony danych. Podaj wartość dla tego parametru, jeśli chcesz określić format dodatkowych informacji poza określonej przez format schowka `cfFormat`. Jeśli jest **NULL**, zostaną użyte wartości domyślne dla innych pól **FORMATETC** struktury.  
  
### <a name="remarks"></a>Uwagi  
 [OnSetData](#onsetdata) wywoływane przez platformę w takim przypadku. Tylko jest używana, gdy w ramach zwraca źródła danych z [COleServerItem::GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource). Jeśli `DelaySetData` nie jest wywoływany z `OnSetData` nigdy nie zostanie wywołana funkcja. `DelaySetData`powinna być wywoływana dla każdej Schowka lub **FORMATETC** format obsługiwanych.  
  
 Aby uzyskać więcej informacji, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) w zestawie Windows SDK.  
  
##  <a name="dodragdrop"></a>COleDataSource::DoDragDrop  
 Wywołanie `DoDragDrop` funkcji członkowskiej do wykonywania operacji przeciągania i upuszczania dla tego źródła danych, zwykle w [CWnd::OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) programu obsługi.  
  
```  
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,  
    LPCRECT lpRectStartDrag = NULL,  
    COleDropSource* pDropSource = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwEffects`  
 Przeciągnij i upuść operacje, które są dozwolone w tym źródle danych. Może to być jeden lub więcej z następujących czynności:  
  
- `DROPEFFECT_COPY`Można wykonać operacji kopiowania.  
  
- `DROPEFFECT_MOVE`Można wykonać operacji przenoszenia.  
  
- `DROPEFFECT_LINK`Link z porzuconych danych do oryginalnych danych było możliwe.  
  
- `DROPEFFECT_SCROLL`Wskazuje, że może wystąpić przewijania operacji przeciągania.  
  
 `lpRectStartDrag`  
 Wskaźnik do prostokąt, który określa, gdzie faktycznie uruchamia przeciągania. Aby uzyskać więcej informacji zobacz następujące sekcji uwag.  
  
 *pDropSource*  
 Wskazuje źródło porzucenia. Jeśli **NULL** następnie domyślną implementację [COleDropSource](../../mfc/reference/coledropsource-class.md) będą używane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Efekt wygenerowanych przez operację przeciągania i upuszczania; w przeciwnym razie `DROPEFFECT_NONE` Jeśli nigdy nie rozpocznie się wykonywanie operacji, ponieważ użytkownik wydane przycisk myszy przed opuszczeniem podany prostokąt.  
  
### <a name="remarks"></a>Uwagi  
 Operacja przeciągania i upuszczania nie rozpoczyna się natychmiast. Oczekuje, aż wskaźnik myszy opuści prostokąt określony przez `lpRectStartDrag` lub dopóki nie upłynie określoną liczbę milisekund. Jeśli `lpRectStartDrag` jest **NULL**, rozmiar prostokąta jest jeden piksel.  
  
 Czas opóźnienia jest określany przez ustawienie klucza rejestru. Można zmienić czas opóźnienia, wywołując [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) lub [CWinApp::WriteProfileInt](../../mfc/reference/cwinapp-class.md#writeprofileint). Jeśli nie określisz czas opóźnienia, jest używana wartość domyślna 200 ms. Czas opóźnienia przeciągania są przechowywane w następujący sposób:  
  
-   Czas opóźnienia przeciągania systemu Windows NT jest przechowywany w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Czas opóźnienia przeciągania 3.x systemu Windows są przechowywane w Windows. Plik INI sekcji [Windows}.  
  
-   Czas opóźnienia przeciągania Windows 95/98 są przechowywane w pamięci podręcznej wersji systemu Windows. INI.  
  
 Dla przeciągnij więcej informacji na temat opóźnienie informacje są przechowywane w rejestrze albo lub. Plik INI, zobacz [WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz artykuł [przeciąganie i upuszczanie: Implementowanie źródłowego porzucić](../../mfc/drag-and-drop-implementing-a-drop-source.md).  
  
##  <a name="empty"></a>COleDataSource::Empty  
 Wywołanie tej funkcji pustą `COleDataSource` obiektu danych.  
  
```  
void Empty();
```  
  
### <a name="remarks"></a>Uwagi  
 Zarówno w pamięci podręcznej i opóźnienie formatów renderowania zostały opróżnione, więc może nastąpić.  
  
 Aby uzyskać więcej informacji, zobacz [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) w zestawie Windows SDK.  
  
##  <a name="flushclipboard"></a>COleDataSource::FlushClipboard  
 Renderuje dane do Schowka, a następnie umożliwia wklejenie danych ze Schowka po zamknięciu aplikacji.  
  
```  
static void PASCAL FlushClipboard();
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj [Funkcja SetClipboard](#setclipboard) umieszczać dane w Schowku.  
  
##  <a name="getclipboardowner"></a>COleDataSource::GetClipboardOwner  
 Określa, czy dane w Schowku zmienił się od [Funkcja SetClipboard](#setclipboard) ostatnio została wywołana, a jeśli tak, określa bieżącego właściciela.  
  
```  
static COleDataSource* PASCAL GetClipboardOwner();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Źródło danych w Schowku, lub **NULL** czy nie ma nic do Schowka, czy aplikacja wywołująca nie posiada Schowka.  
  
##  <a name="onrenderdata"></a>COleDataSource::OnRenderData  
 Wywoływane przez platformę, by pobrać dane w określonym formacie.  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury, określając format, w którym jest wymagane informacje.  
  
 `lpStgMedium`  
 Wskazuje [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury, w którym ma zostać zwrócone dane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Określony format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](#delayrenderdata) lub [DelayRenderFileData](#delayrenderfiledata) funkcji członkowskiej do renderowania opóźnione. Domyślna implementacja tej funkcji będzie wywoływać [OnRenderFileData](#onrenderfiledata) lub [OnRenderGlobalData](#onrenderglobaldata) Jeśli podany nośnik jest odpowiednio pliku lub pamięci. Jeśli żadna z tych formatów są dostarczane, domyślna implementacja będzie zwracać 0 i nic nie rób. Aby uzyskać więcej informacji na opóźnione renderowanie, ponieważ obsługiwane przez MFC, zobacz artykuł [obiekty danych i źródła danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Jeśli `lpStgMedium` ->  *tymed* jest **TYMED_NULL**, **STGMEDIUM** powinny być przydzielone i wypełnione określony przez *lpFormatEtc -> tymed*. Jeśli nie jest **TYMED_NULL**, **STGMEDIUM** powinno być wypełnione w miejscu z danymi.  
  
 Jest to zaawansowane możliwym do zastąpienia. Należy przesłonić tę funkcję, aby przekazać dane w formacie żądanego i średnia liczba godzin. W zależności od danych warto override jednego z innych wersji tej funkcji. Jeśli dane są małe i stały rozmiar, Zastąp `OnRenderGlobalData`. Jeśli znajduje się w pliku danych lub o rozmiarze zmiennej, Zastąp `OnRenderFileData`.  
  
 Aby uzyskać więcej informacji, zobacz [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) i [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury, [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) typ wyliczeniowy i [Metoda IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) w systemie Windows SDK.  
  
##  <a name="onrenderfiledata"></a>COleDataSource::OnRenderFileData  
 Wywoływane przez platformę, by pobrać dane w określonym formacie, gdy określony nośnik to plik.  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury, określając format, w którym jest wymagane informacje.  
  
 `pFile`  
 Wskazuje [cfile —](../../mfc/reference/cfile-class.md) obiektu, w którym ma być renderowany danych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Określony format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](#delayrenderdata) funkcji członkowskiej do renderowania opóźnione. Domyślna implementacja tej funkcji po prostu zwraca **FALSE**.  
  
 Jest to zaawansowane możliwym do zastąpienia. Należy przesłonić tę funkcję, aby przekazać dane w formacie żądanego i średnia liczba godzin. W zależności od danych warto override jednego z innych wersji tej funkcji. Jeśli chcesz obsługiwać wiele nośników, Zastąp [OnRenderData](#onrenderdata). Jeśli znajduje się w pliku danych lub o rozmiarze zmiennej, Zastąp `OnRenderFileData`. Aby uzyskać więcej informacji na opóźnione renderowanie, ponieważ obsługiwane przez MFC, zobacz artykuł [obiekty danych i źródła danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Aby uzyskać więcej informacji, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury i [Metoda IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) w zestawie Windows SDK.  
  
##  <a name="onrenderglobaldata"></a>COleDataSource::OnRenderGlobalData  
 Wywoływane przez platformę, by pobrać dane w określonym formacie po określonym nośnik pamięci globalnej.  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury, określając format, w którym jest wymagane informacje.  
  
 `phGlobal`  
 Wskazuje dojścia do globalnej pamięci, w którym ma zostać zwrócone dane. Jeśli jeden nie jeszcze przydzielono, ten parametr może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Określony format jest jednym wcześniej umieszczone w `COleDataSource` przy użyciu [DelayRenderData](#delayrenderdata) funkcji członkowskiej do renderowania opóźnione. Domyślna implementacja tej funkcji po prostu zwraca **FALSE**.  
  
 Jeśli `phGlobal` jest **NULL**, następnie nowy `HGLOBAL` powinny być przydzielone i zwracany w `phGlobal`. W przeciwnym razie `HGLOBAL` określonego przez `phGlobal` powinno być wypełnione z danymi. Ilość danych umieszczone w `HGLOBAL` nie może przekraczać bieżący rozmiar bloku pamięci. Ponadto nie można przydzielić bloku, aby większy rozmiar.  
  
 Jest to zaawansowane możliwym do zastąpienia. Należy przesłonić tę funkcję, aby przekazać dane w formacie żądanego i średnia liczba godzin. W zależności od danych warto override jednego z innych wersji tej funkcji. Jeśli chcesz obsługiwać wiele nośników, Zastąp [OnRenderData](#onrenderdata). Jeśli znajduje się w pliku danych lub o rozmiarze zmiennej, Zastąp [OnRenderFileData](#onrenderfiledata). Aby uzyskać więcej informacji na opóźnione renderowanie, ponieważ obsługiwane przez MFC, zobacz artykuł [obiekty danych i źródła danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Aby uzyskać więcej informacji, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury i [Metoda IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) w zestawie Windows SDK.  
  
##  <a name="onsetdata"></a>COleDataSource::OnSetData  
 Wywoływane przez platformę, by ustawić lub podmienić dane w `COleDataSource` obiekt w określonym formacie.  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>Parametry  
 `lpFormatEtc`  
 Wskazuje [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury, określając format, w którym dane są zastępowane.  
  
 `lpStgMedium`  
 Wskazuje [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) struktury zawierającej dane, które zastąpi bieżącą zawartość `COleDataSource` obiektu.  
  
 `bRelease`  
 Wskazuje, kto jest właścicielem nośnik po zakończeniu wywołania funkcji. Obiekt wywołujący decyduje, kto jest odpowiedzialny za zwolnienie zasobów przydzielonych imieniu nośnika magazynowania. Obiekt wywołujący robi to przez ustawienie `bRelease`. Jeśli `bRelease` jest różna od zera, źródła danych przejmuje, zwalnianie nośnik, po zakończeniu używania go. Gdy `bRelease` ma wartość 0, wywołujący zachowuje własność i źródła danych można użyć nośnik tylko na czas trwania wywołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Źródło danych dopiero po właściciela danych został pomyślnie uzyskano go. Oznacza to, że nie trwa własność Jeśli `OnSetData` zwraca wartość 0. Jeśli źródło danych przejmuje, zwalnia nośnik wywołując [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) funkcji.  
  
 Domyślna implementacja nie działa. Należy przesłonić tę funkcję, aby zamienić dane w określonym formacie. Jest to zaawansowane możliwym do zastąpienia.  
  
 Aby uzyskać więcej informacji, zobacz [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) i [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury i [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) i [Metoda IDataObject::GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) funkcje w zestawie Windows SDK.  
  
##  <a name="setclipboard"></a>COleDataSource::SetClipboard  
 Umieszcza dane zawarte w `COleDataSource` obiektu w Schowku po wywołaniu metody jedną z następujących funkcji: [CacheData](#cachedata), [CacheGlobalData](#cacheglobaldata), [DelayRenderData](#delayrenderdata), lub [DelayRenderFileData](#delayrenderfiledata).  
  
```  
void SetClipboard();
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Przykładowe MFC OCLIENT](../../visual-cpp-samples.md)   
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDataObject](../../mfc/reference/coledataobject-class.md)
