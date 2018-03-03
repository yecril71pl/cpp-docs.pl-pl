---
title: Klasa COleConvertDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleConvertDialog
- AFXODLGS/COleConvertDialog
- AFXODLGS/COleConvertDialog::COleConvertDialog
- AFXODLGS/COleConvertDialog::DoConvert
- AFXODLGS/COleConvertDialog::DoModal
- AFXODLGS/COleConvertDialog::GetClassID
- AFXODLGS/COleConvertDialog::GetDrawAspect
- AFXODLGS/COleConvertDialog::GetIconicMetafile
- AFXODLGS/COleConvertDialog::GetSelectionType
- AFXODLGS/COleConvertDialog::m_cv
dev_langs:
- C++
helpviewer_keywords:
- COleConvertDialog [MFC], COleConvertDialog
- COleConvertDialog [MFC], DoConvert
- COleConvertDialog [MFC], DoModal
- COleConvertDialog [MFC], GetClassID
- COleConvertDialog [MFC], GetDrawAspect
- COleConvertDialog [MFC], GetIconicMetafile
- COleConvertDialog [MFC], GetSelectionType
- COleConvertDialog [MFC], m_cv
ms.assetid: a7c57714-31e8-4b78-834d-8ddd1b856a1c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f93c17416c81d4c152608f4d8a8b78f48e5422c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coleconvertdialog-class"></a>Klasa COleConvertDialog
Aby uzyskać więcej informacji, zobacz [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) struktury w zestawie Windows SDK.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleConvertDialog : public COleDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleConvertDialog::COleConvertDialog](#coleconvertdialog)|Konstruuje `COleConvertDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleConvertDialog::DoConvert](#doconvert)|Wykonuje konwersję określony w oknie dialogowym.|  
|[COleConvertDialog::DoModal](#domodal)|Wyświetla okno dialogowe elementu OLE zmiany.|  
|[COleConvertDialog::GetClassID](#getclassid)|Pobiera **CLSID** skojarzone z wybranego elementu.|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Określa, czy do rysowania elementu w postaci ikony.|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera dojścia do metaplik skojarzonych z formularzem ikony, tego elementu.|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Pobiera typ wyboru dokonanego.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|Struktura, która steruje zachowaniem w oknie dialogowym.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Kod kontenera generowane przez Kreatora aplikacji korzysta z tej klasy.  
  
 Aby uzyskać informacje o oknach dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="coleconvertdialog"></a>COleConvertDialog::COleConvertDialog  
 Tworzy tylko `COleConvertDialog` obiektu.  
  
```  
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Punkty elementu, który ma zostać poddany konwersji lub aktywowane.  
  
 `dwFlags`  
 Tworzenie flagę zawiera dowolną liczbę następujące wartości łączyć, używając operatora testu koniunkcji- lub operator:  
  
- **CF_SELECTCONVERTTO** Określa, że przycisk radiowy Konwertuj na wybrany zostanie początkowo wywołanego okna dialogowego. Domyślnie włączone.  
  
- **CF_SELECTACTIVATEAS** Określa, że przycisk radiowy aktywować jako wybrany zostanie początkowo wywołanego okna dialogowego.  
  
- **CF_SETCONVERTDEFAULT** Określa, że klasa których **CLSID** jest określona przez **clsidConvertDefault** członkiem `m_cv` struktura będzie służyć jako domyślny Zaznaczenie w polu listy klasy, jeśli Konwertuj na przycisk radiowy jest zaznaczony.  
  
- **CF_SETACTIVATEDEFAULT** Określa, że klasa których **CLSID** jest określona przez **clsidActivateDefault** członkiem `m_cv` struktura będzie służyć jako domyślny Zaznaczenie w polu listy klas podczas aktywowania jako przycisk radiowy jest zaznaczony.  
  
- **CF_SHOWHELPBUTTON** Określa, czy przycisk Pomoc, aby będą wyświetlane, gdy jest wywoływana w oknie dialogowym.  
  
 `pClassID`  
 Wskazuje identyfikator CLSID elementu, który ma zostać poddany konwersji lub aktywowane. Jeśli **NULL**, **CLSID** skojarzone z `pItem` będą używane.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okno nadrzędne, okno dialogowe ma ustawioną wartość okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić okno dialogowe, wywołaj [DoModal](#domodal) funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [klucz CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) i [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) struktury.  
  
##  <a name="doconvert"></a>COleConvertDialog::DoConvert  
 Wywołanie tej funkcji po powrocie pomyślnie z [DoModal](#domodal), albo do konwersji do typu obiektu aktywacji [COleClientItem](../../mfc/reference/coleclientitem-class.md).  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Punkty elementu, który ma zostać poddany konwersji lub aktywowane. Nie może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Element jest konwertowane lub aktywowaną zgodnie z wybranych przez użytkownika w oknie dialogowym Konwertuj informacje.  
  
##  <a name="domodal"></a>COleConvertDialog::DoModal  
 Wywołanie tej funkcji, aby wyświetlić okno dialogowe Konwertowanie OLE.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:  
  
- **IDOK** Jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- **IDCANCEL** Jeśli użytkownik anulował okno dialogowe.  
  
- **IDABORT** Jeśli wystąpił błąd. Jeśli **IDABORT** jest zwracany, wywołaj [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcji członkowskiej, aby uzyskać więcej informacji o typie wystąpił błąd. Aby uzyskać listę możliwych błędów, zobacz [OleUIConvert](http://msdn.microsoft.com/library/windows/desktop/ms680694) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych formantów okna dialogowego przez ustawienie członkami [m_cv](#m_cv) struktury, ten krok należy wykonać przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca **IDOK**, innego członka można wywołać funkcji, aby uzyskać ustawienia i informacje, które zostało wprowadzone przez użytkownika do okna dialogowego.  
  
##  <a name="getclassid"></a>COleConvertDialog::GetClassID  
 Wywołanie tej funkcji, aby uzyskać **CLSID** skojarzone z elementem wybrany w oknie dialogowym Konwertuj przez użytkownika.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **CLSID** skojarzony z elementem, który został wybrany w oknie dialogowym Convert.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca **IDOK**.  
  
 Aby uzyskać więcej informacji, zobacz [klucz CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) w zestawie Windows SDK.  
  
##  <a name="getdrawaspect"></a>COleConvertDialog::GetDrawAspect  
 Wywołanie tej funkcji w celu ustalenia, czy użytkownik wybrał opcję Wyświetl zaznaczony element jako ikonę.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Metoda wymagane do renderowania obiektu.  
  
- `DVASPECT_CONTENT`Zwracany, jeśli nie zaznaczono pola wyboru Wyświetl jako ikonę.  
  
- `DVASPECT_ICON`Zwracany, jeśli zaznaczono pole wyboru Wyświetl jako ikonę.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji tylko po [DoModal](#domodal) zwraca **IDOK**.  
  
 Aby uzyskać więcej informacji na rysunku aspekt, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury danych w zestawie Windows SDK.  
  
##  <a name="geticonicmetafile"></a>COleConvertDialog::GetIconicMetafile  
 Wywołanie tej funkcji można uzyskać dojścia do Metaplik zawierający odpowiednikiem aspekt wybranego elementu.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do Metaplik zawierający odpowiednikiem aspekt wybranego elementu, jeśli pole wyboru Wyświetl jako ikonę sprawdzane podczas okna dialogowego zostało odrzucone, wybierając **OK**; w przeciwnym razie **NULL**.  
  
##  <a name="getselectiontype"></a>COleConvertDialog::GetSelectionType  
 Wywołanie tej funkcji można określić typu konwersji wybrany w oknie dialogowym Convert.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ wybranego.  
  
### <a name="remarks"></a>Uwagi  
 Zwracany typ wartości są określane przez **wybór** typ wyliczeniowy zadeklarowany w `COleConvertDialog` klasy.  
  
```  
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };  
```  
  
 Wykonaj krótkie opisy z następujących wartości:  
  
- **COleConvertDialog::noConversion** zwrócił Jeśli okno dialogowe została anulowana lub użytkownik wybrał brak konwersji. Jeśli `COleConvertDialog::DoModal` zwrócił **IDOK**, istnieje możliwość, że użytkownik wybrał inną ikonę niż wcześniej wybrane.  
  
- **COleConvertDialog::convertItem** zwrócony, jeśli zaznaczono przycisk radiowy Konwertuj na, użytkownik wybrał inny element, aby przekonwertować, a `DoModal` zwrócił **IDOK**.  
  
- **COleConvertDialog::activateAs** zwrócony, jeśli zaznaczono przycisk radiowy aktywować jako, użytkownik wybrał inny element, aby aktywować, i `DoModal` zwrócił **IDOK**.  
  
##  <a name="m_cv"></a>COleConvertDialog::m_cv  
 Struktura typu **OLEUICONVERT** służące do sterowania zachowaniem okna dialogowego Convert.  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie tej konstrukcji może być modyfikowany bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
