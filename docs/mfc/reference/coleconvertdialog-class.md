---
title: Klasa COleConvertDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd2b9e09ed536d30729d39d53dc983d02cf0c6d7
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849690"
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
|[COleConvertDialog::DoConvert](#doconvert)|Wykonuje konwersję określone w oknie dialogowym.|  
|[COleConvertDialog::DoModal](#domodal)|Wyświetla okna dialogowego OLE Zmień element.|  
|[COleConvertDialog::GetClassID](#getclassid)|Pobiera identyfikator CLSID skojarzone z wybranym elementem.|  
|[COleConvertDialog::GetDrawAspect](#getdrawaspect)|Określa, czy do rysowania elementu jako ikona.|  
|[COleConvertDialog::GetIconicMetafile](#geticonicmetafile)|Pobiera uchwyt do metaplik skojarzony z formularzem ikony tego elementu.|  
|[COleConvertDialog::GetSelectionType](#getselectiontype)|Pobiera typ wyboru dokonanego.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleConvertDialog::m_cv](#m_cv)|Struktura, która steruje zachowaniem okno dialogowe.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Kod kontenera generowane przez Kreatora aplikacji korzysta z tej klasy.  
  
 Aby uzyskać więcej informacji o okna dialogowe OLE specyficzne artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleConvertDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="coleconvertdialog"></a>  COleConvertDialog::COleConvertDialog  
 Tworzy tylko `COleConvertDialog` obiektu.  
  
```  
explicit COleConvertDialog (
    COleClientItem* pItem,
    DWORD dwFlags = CF_SELECTCONVERTTO,
    CLSID* pClassID = NULL,
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pItem*  
 Wskazuje element które mają zostać poddany konwersji lub aktywowane.  
  
 *Flagidw*  
 Flagi tworzenia zawiera dowolną liczbę następujące wartości łączyć, używając operatora testu koniunkcji — lub operator:  
  
- CF_SELECTCONVERTTO Określa, że będzie przycisk radiowy Konwertuj na wybrany początkowo, gdy okno dialogowe jest wywoływana. Domyślnie włączone.  
  
- CF_SELECTACTIVATEAS Określa, że przycisk radiowy aktywować jako będzie można wybrać początkowo, gdy okno dialogowe jest wywoływana.  
  
- CF_SETCONVERTDEFAULT Określa, że klasy, którego identyfikator CLSID jest określona przez `clsidConvertDefault` członkiem `m_cv` struktura będzie służyć jako domyślny wybór w polu listy klas, po wybraniu przycisku radiowego Konwertuj na.  
  
- CF_SETACTIVATEDEFAULT Określa, że klasy, którego identyfikator CLSID jest określona przez `clsidActivateDefault` członkiem `m_cv` struktura będzie służyć jako domyślny wybór w polu listy klas aktywować jako zaznaczona jest opcja.  
  
- CF_SHOWHELPBUTTON Określa, że przycisk Pomoc, będą wyświetlane, gdy wywoływana jest okno dialogowe.  
  
 *pClassID*  
 Wskazuje identyfikator CLSID programu element które mają zostać poddany konwersji lub aktywowane. Jeśli ma wartość NULL, skojarzony identyfikator CLSID *pItem* będą używane.  
  
 *pParentWnd*  
 Wskazuje na obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne, okno dialogowe jest ustawiony na okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Aby wyświetlić okno dialogowe, należy wywołać [DoModal](#domodal) funkcji.  
  
 Aby uzyskać więcej informacji, zobacz [klucz identyfikator CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) i [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) struktury.  
  
##  <a name="doconvert"></a>  COleConvertDialog::DoConvert  
 Wywołaj tę funkcję, po powrocie pomyślnie ze [DoModal](#domodal), albo, aby przekonwertować lub Aktywuj obiekt typu [COleClientItem](../../mfc/reference/coleclientitem-class.md).  
  
```  
BOOL DoConvert(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pItem*  
 Wskazuje element które mają zostać poddany konwersji lub aktywowane. Nie może mieć wartości NULL.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Element jest konwertowany lub aktywowaną zgodnie z informacji wybrane przez użytkownika w oknie dialogowym konwersji.  
  
##  <a name="domodal"></a>  COleConvertDialog::DoModal  
 Wywołaj tę funkcję, aby wyświetlić okno dialogowe Konwertowanie OLE.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jeden z następujących wartości:  
  
- IDOK, jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- IDCANCEL, jeśli użytkownik anulował okno dialogowe.  
  
- IDABORT, jeśli wystąpił błąd. Jeśli zwracana jest IDABORT, wywołaj [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcja elementu członkowskiego, aby uzyskać więcej informacji o typie błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIConvert](http://msdn.microsoft.com/library/windows/desktop/ms680694) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Aby inicjowanie różne formanty okna dialogowego, ustawiając członkowie [m_cv](#m_cv) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.  
  
 Jeśli `DoModal` zwraca IDOK, może wywołać inny członek funkcje, które można pobrać ustawień lub informacje, które zostało wprowadzone przez użytkownika do okna dialogowego.  
  
##  <a name="getclassid"></a>  COleConvertDialog::GetClassID  
 Wywołanie tę funkcję, aby uzyskać identyfikator CLSID skojarzonego z elementu wybranego w oknie dialogowym konwersji użytkownika.  
  
```  
REFCLSID GetClassID() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator CLSID skojarzone z elementem, który został wybrany w oknie dialogowym konwersji.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji dopiero po [DoModal](#domodal) zwraca IDOK.  
  
 Aby uzyskać więcej informacji, zobacz [klucz identyfikator CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) w zestawie Windows SDK.  
  
##  <a name="getdrawaspect"></a>  COleConvertDialog::GetDrawAspect  
 Wywołaj tę funkcję, aby ustalić, czy użytkownik wybrał opcję wyświetlić wybranego elementu w postaci ikony.  
  
```  
DVASPECT GetDrawAspect() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Metoda wymagane do renderowania obiektu.  
  
- DVASPECT_CONTENT zwracany, jeśli nie zaznaczono pola wyboru Wyświetl jako ikonę.  
  
- DVASPECT_ICON zwracany, jeśli zaznaczono pole wyboru Wyświetl jako ikonę.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji dopiero po [DoModal](#domodal) zwraca IDOK.  
  
 Aby uzyskać więcej informacji na temat Rysowanie aspektu, zobacz [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) struktury danych w zestawie Windows SDK.  
  
##  <a name="geticonicmetafile"></a>  COleConvertDialog::GetIconicMetafile  
 Wywołaj tę funkcję można pobrać uchwytu do metaplik, który zawiera ikony aspektów wybranego elementu.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Dojście do Metaplik zawierający ikony aspektów wybranego elementu, jeśli była wyświetlana jako ikona okno wyboru zaznaczone, gdy okno dialogowe został odrzucony po wybraniu przycisku OK; w przeciwnym razie wartość NULL.  
  
##  <a name="getselectiontype"></a>  COleConvertDialog::GetSelectionType  
 Wywołaj tę funkcję, aby określić typ konwersji wybrane w oknie dialogowym konwersji.  
  
```  
UINT GetSelectionType() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ dokonano wyboru.  
  
### <a name="remarks"></a>Uwagi  
 Wartości zwracanej są określane przez `Selection` typ wyliczeniowy zadeklarowany w `COleConvertDialog` klasy.  
  
```  
enum Selection {
    noConversion,
    convertItem,
    activateAs
    };  
```  
  
 Wykonaj krótkie opisy tych wartości:  
  
- `COleConvertDialog::noConversion` Zwracany, jeśli okno dialogowe zostało anulowane lub konwersja nie jest wybrany przez użytkownika. Jeśli `COleConvertDialog::DoModal` zwrócone IDOK, jest możliwe, że użytkownik wybrał inną ikonę niż wcześniej wybrany.  
  
- `COleConvertDialog::convertItem` Zwracany, jeśli przycisk radiowy Konwertuj na zostało zaznaczone, użytkownik wybrał inny element, aby przekonwertować, a `DoModal` zwrócił IDOK.  
  
- `COleConvertDialog::activateAs` Zwracany, jeśli przycisk radiowy aktywować jako zostało zaznaczone, użytkownik wybrał inny element, aby aktywować, i `DoModal` zwrócił IDOK.  
  
##  <a name="m_cv"></a>  COleConvertDialog::m_cv  
 Struktura OLEUICONVERT służące do sterowania zachowaniem okna dialogowego konwersji typu.  
  
```  
OLEUICONVERT m_cv;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie tej struktury można zmodyfikować bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUICONVERT](http://msdn.microsoft.com/library/windows/desktop/ms686657) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
