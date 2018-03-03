---
title: Klasa COlePasteSpecialDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::COlePasteSpecialDialog
- AFXODLGS/COlePasteSpecialDialog::AddFormat
- AFXODLGS/COlePasteSpecialDialog::AddLinkEntry
- AFXODLGS/COlePasteSpecialDialog::AddStandardFormats
- AFXODLGS/COlePasteSpecialDialog::CreateItem
- AFXODLGS/COlePasteSpecialDialog::DoModal
- AFXODLGS/COlePasteSpecialDialog::GetDrawAspect
- AFXODLGS/COlePasteSpecialDialog::GetIconicMetafile
- AFXODLGS/COlePasteSpecialDialog::GetPasteIndex
- AFXODLGS/COlePasteSpecialDialog::GetSelectionType
- AFXODLGS/COlePasteSpecialDialog::m_ps
dev_langs:
- C++
helpviewer_keywords:
- COlePasteSpecialDialog [MFC], COlePasteSpecialDialog
- COlePasteSpecialDialog [MFC], AddFormat
- COlePasteSpecialDialog [MFC], AddLinkEntry
- COlePasteSpecialDialog [MFC], AddStandardFormats
- COlePasteSpecialDialog [MFC], CreateItem
- COlePasteSpecialDialog [MFC], DoModal
- COlePasteSpecialDialog [MFC], GetDrawAspect
- COlePasteSpecialDialog [MFC], GetIconicMetafile
- COlePasteSpecialDialog [MFC], GetPasteIndex
- COlePasteSpecialDialog [MFC], GetSelectionType
- COlePasteSpecialDialog [MFC], m_ps
ms.assetid: 0e82ef9a-9bbe-457e-8240-42c86a0534f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8680842f0aeeebf98eabc0f278089781290ad902
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="colepastespecialdialog-class"></a>Klasa COlePasteSpecialDialog
Używane dla okna dialogowego OLE Wklej specjalne.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COlePasteSpecialDialog : public COleDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COlePasteSpecialDialog::COlePasteSpecialDialog](#colepastespecialdialog)|Konstruuje `COlePasteSpecialDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COlePasteSpecialDialog::AddFormat](#addformat)|Dodaje niestandardowe formaty do listy formatów, które można wkleić aplikacji.|  
|[COlePasteSpecialDialog::AddLinkEntry](#addlinkentry)|Dodaje nowy wpis do listy obsługiwanych formatów Schowka.|  
|[COlePasteSpecialDialog::AddStandardFormats](#addstandardformats)|Dodaje **CF_BITMAP**, **CF_DIB**, `CF_METAFILEPICT`i opcjonalnie `CF_LINKSOURCE` do listy formatów można wkleić aplikacji.|  
|[COlePasteSpecialDialog::CreateItem](#createitem)|Tworzy element w dokumencie kontenera w określonym formacie.|  
|[COlePasteSpecialDialog::DoModal](#domodal)|Wyświetla okno dialogowe w OLE Wklej specjalne.|  
|[COlePasteSpecialDialog::GetDrawAspect](#getdrawaspect)|Informuje, czy ma zostać narysowany element jako ikony lub nie.|  
|[COlePasteSpecialDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera dojścia do metaplik skojarzonych z formularzem ikony, tego elementu.|  
|[COlePasteSpecialDialog::GetPasteIndex](#getpasteindex)|Pobiera indeks Wklej dostępne opcje, który został wybrany przez użytkownika.|  
|[COlePasteSpecialDialog::GetSelectionType](#getselectiontype)|Pobiera typ wyboru dokonanego.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COlePasteSpecialDialog::m_ps](#m_ps)|Struktura typu **OLEUIPASTESPECIAL** steruje funkcja okna dialogowego.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz obiekt klasy `COlePasteSpecialDialog` umożliwia wywołanie tego okna dialogowego. Po `COlePasteSpecialDialog` obiekt został skonstruowany, możesz użyć [AddFormat](#addformat) i [AddStandardFormats](#addstandardformats) funkcji elementów członkowskich, aby dodać formaty Schowka do okna dialogowego. Można również użyć [m_ps](#m_ps) struktury zainicjować wartości lub stany formantów w oknie dialogowym. `m_ps` Struktura jest typu **OLEUIPASTESPECIAL**.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji dotyczących okien dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePasteSpecialDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="addformat"></a>COlePasteSpecialDialog::AddFormat  
 Wywołanie tej funkcji, aby dodać nowy format lista formatów obsługiwanych przez aplikację w ramach operacji Wklej specjalne.  
  
```  
void AddFormat(
    const FORMATETC& formatEtc,  
    LPTSTR lpszFormat,  
    LPTSTR lpszResult,  
    DWORD flags);

 
void AddFormat(
    UINT cf,  
    DWORD tymed,  
    UINT nFormatID,  
    BOOL bEnableIcon,  
    BOOL bLink);
```  
  
### <a name="parameters"></a>Parametry  
 *formatowaniu*  
 Odwołanie do typu danych do dodania.  
  
 `lpszFormat`  
 Ciąg opisujący formatu dla użytkownika.  
  
 *lpszResult*  
 Ciąg opisujący wynik ten format jest wybrany w oknie dialogowym.  
  
 `flags`  
 Różne łączenie i osadzanie opcji dostępnych dla tego formatu. Ta flaga jest bitowe połączenie co najmniej jednego różne wartości w **OLEUIPASTEFLAG** typ wyliczeniowy.  
  
 `cf`  
 Format schowka do dodania.  
  
 *tymed*  
 Typy nośniki dostępne w tym formacie. Jest to bitowe połączenie co najmniej jedną z wartości w **TYMED** typ wyliczeniowy.  
  
 `nFormatID`  
 Identyfikator ciągu, która identyfikuje ten format. Format ten ciąg jest dwa oddzielne ciągi oddzielone znakiem "\n". Pierwszy ciąg jest taki sam, które zostaną przekazane w *lpstrFormat* parametr, a drugi jest taka sama jak *lpstrResult* parametru.  
  
 *bEnableIcon*  
 Flaga określająca, czy pole wyboru Wyświetl jako ikonę jest włączone, gdy ten format jest wybierany w polu listy.  
  
 *bLink*  
 Flaga określająca, czy przycisk radiowy Wklej łącze jest włączone, gdy ten format jest wybierany w polu listy.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja wywoływana, aby dodać albo standardowych formatów, takich jak **CF_TEXT** lub **CF_TIFF** lub niestandardowe formaty zarejestrowanych w aplikacji w systemie. Aby uzyskać więcej informacji na temat wklejania obiektów danych do aplikacji, zobacz artykuł [obiekty danych i źródła danych: manipulowanie](../../mfc/data-objects-and-data-sources-manipulation.md).  
  
 Aby uzyskać więcej informacji, zobacz [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) typ wyliczeniowy i [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) wyliczyć typów w zestawie Windows SDK.  
  
##  <a name="addlinkentry"></a>COlePasteSpecialDialog::AddLinkEntry  
 Dodaje nowy wpis do listy obsługiwanych formatów Schowka.  
  
```  
OLEUIPASTEFLAG AddLinkEntry(UINT cf);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 Format schowka do dodania.  
  
### <a name="return-value"></a>Wartość zwracana  
 [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) struktury zawierającej informacje dotyczące nowego wpisu łącza.  
  
##  <a name="addstandardformats"></a>COlePasteSpecialDialog::AddStandardFormats  
 Wywołanie tej funkcji, aby dodać następujące formaty Schowka do listy formatów obsługiwanych przez aplikację w ramach operacji Wklej specjalne:  
  
```  
void AddStandardFormats(BOOL bEnableLink = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bEnableLink*  
 Flaga określająca, czy dodać `CF_LINKSOURCE` do listy formatów można wkleić aplikacji.  
  
### <a name="remarks"></a>Uwagi  
  
- **CF_BITMAP**  
  
- **CF_DIB**  
  
- `CF_METAFILEPICT`  
  
- **"Osadzonego"**  
  
-   (opcjonalnie) **"Link źródła"**  
  
 Te formaty są używane do obsługi osadzanie i łączenie.  
  
##  <a name="colepastespecialdialog"></a>COlePasteSpecialDialog::COlePasteSpecialDialog  
 Konstruuje `COlePasteSpecialDialog` obiektu.  
  
```  
COlePasteSpecialDialog(
    DWORD dwFlags = PSF_SELECTPASTE,  
    COleDataObject* pDataObject = NULL,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Flagi tworzenia zawiera dowolną liczbę następujące flagi łączyć, używając operator Alternatywy:  
  
- `PSF_SELECTPASTE`Określa, że przycisk radiowy Wklej będą sprawdzane początkowo wywołanego okna dialogowego. Nie można używać w połączeniu z `PSF_SELECTPASTELINK`. Domyślnie włączone.  
  
- `PSF_SELECTPASTELINK`Określa początkowo zaznaczone Wklej łącze przycisk radiowy będzie wówczas, gdy jest wywoływana okna dialogowego. Nie można używać w połączeniu z `PSF_SELECTPASTE`.  
  
- `PSF_CHECKDISPLAYASICON`Określa, że pole wyboru Wyświetl jako ikonę będą sprawdzane początkowo wywołanego okna dialogowego.  
  
- `PSF_SHOWHELP`Określa, czy przycisk Pomoc, aby będą wyświetlane, gdy jest wywoływana w oknie dialogowym.  
  
 `pDataObject`  
 Wskazuje [COleDataObject](../../mfc/reference/coledataobject-class.md) wklejania. Jeśli ta wartość jest **NULL**, pobiera `COleDataObject` ze Schowka.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okno nadrzędne, okno dialogowe ma ustawioną wartość okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jedynie tworzy `COlePasteSpecialDialog` obiektu. Aby wyświetlić okno dialogowe, wywołaj [DoModal](#domodal) funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIPASTEFLAG](http://msdn.microsoft.com/library/windows/desktop/ms682172) wyliczyć typów w zestawie Windows SDK.  
  
##  <a name="createitem"></a>COlePasteSpecialDialog::CreateItem  
 Tworzy nowy element, który został wybrany w oknie dialogowym Wklej specjalne.  
  
```  
BOOL CreateItem(COleClientItem* pNewItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pNewItem*  
 Wskazuje `COleClientItem` wystąpienia. Nie może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli została utworzona pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja ta powinna być wywoływana tylko po [DoModal](#domodal) zwraca **IDOK**.  
  
##  <a name="domodal"></a>COlePasteSpecialDialog::DoModal  
 Wyświetla okno dialogowe w OLE Wklej specjalne.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:  
  
- **IDOK** Jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- **IDCANCEL** Jeśli użytkownik anulował okno dialogowe.  
  
- **IDABORT** Jeśli wystąpił błąd. Jeśli **IDABORT** jest zwracany, wywołaj `COleDialog::GetLastError` funkcji członkowskiej, aby uzyskać więcej informacji o typie wystąpił błąd. Aby uzyskać listę możliwych błędów, zobacz [OleUIPasteSpecial](http://msdn.microsoft.com/library/windows/desktop/ms694512) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych formantów okna dialogowego przez ustawienie członkami [m_ps](#m_ps) struktury, ten krok należy wykonać przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca **IDOK**, innego członka można wywołać funkcji można pobrać ustawień lub wprowadzania informacji przez użytkownika w oknie dialogowym.  
  
##  <a name="getdrawaspect"></a>COlePasteSpecialDialog::GetDrawAspect  
 Określa, czy użytkownik wybrał opcję Wyświetl zaznaczony element jako ikonę.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Metoda wymagane do renderowania obiektu.  
  
- `DVASPECT_CONTENT`Zwracany, jeśli pole wyboru Wyświetl jako ikonę nie została sprawdzona odrzucania okna dialogowego.  
  
- `DVASPECT_ICON`Zwracany, jeśli pole wyboru Wyświetl jako ikonę zaznaczono odrzucania okna dialogowego.  
  
### <a name="remarks"></a>Uwagi  
 Tylko wywołanie tej funkcji po [DoModal](#domodal) zwraca **IDOK**.  
  
 Aby uzyskać więcej informacji na rysunku aspekt, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury w zestawie Windows SDK.  
  
##  <a name="geticonicmetafile"></a>COlePasteSpecialDialog::GetIconicMetafile  
 Pobiera metaplików powiązanych z elementem wybrane przez użytkownika.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do Metaplik zawierający odpowiednikiem aspekt wybranego elementu, jeśli pole wyboru Wyświetl jako ikonę wybrano odrzucania okna dialogowego, wybierając **OK**; w przeciwnym razie **NULL**.  
  
##  <a name="getpasteindex"></a>COlePasteSpecialDialog::GetPasteIndex  
 Pobiera wartość indeksu skojarzone z danym wpisem wybrany przez użytkownika.  
  
```  
int GetPasteIndex() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks w tablicy **OLEUIPASTEENTRY** struktur, które zostały wybrane przez użytkownika. Format, który odpowiada wybranego indeksu należy używać podczas wykonywania operacji wklejania.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [OLEUIPASTEENTRY](http://msdn.microsoft.com/library/windows/desktop/ms690165) struktury w zestawie Windows SDK.  
  
##  <a name="getselectiontype"></a>COlePasteSpecialDialog::GetSelectionType  
 Określa typ wybranego użytkownika.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca typ wybranego.  
  
### <a name="remarks"></a>Uwagi  
 Zwracany typ wartości są określane przez **wybór** typ wyliczeniowy zadeklarowany w `COlePasteSpecialDialog` klasy.  
  
```  
enum Selection {
    pasteLink,
    pasteNormal,
    pasteOther,
    pasteStatic
    };  
```  
  
 Wykonaj krótki desccriptions z następujących wartości:  
  
- **COlePasteSpecialDialog::pasteLink** zaznaczono opcję Wklej łącze i standardowym formacie OLE został wybrany format.  
  
- **COlePasteSpecialDialog::pasteNormal** zaznaczono opcję Wklej i standardowym formacie OLE został wybrany format.  
  
- **COlePasteSpecialDialog::pasteOther** wybrany format nie jest standardowym formacie OLE.  
  
- **COlePasteSpecialDialog::pasteStatic** metaplików został wybrany format.  
  
##  <a name="m_ps"></a>COlePasteSpecialDialog::m_ps  
 Struktura typu **OLEUIPASTESPECIAL** służące do sterowania zachowaniem Wklej specjalne okna dialogowego.  
  
```  
OLEUIPASTESPECIAL m_ps;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie tej konstrukcji może być modyfikowany bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIPASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/ms692434) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC OCLIENT](../../visual-cpp-samples.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
