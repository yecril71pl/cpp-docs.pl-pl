---
title: Klasa COleLinksDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
dev_langs:
- C++
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3db235771156380c5f1b22af225d7aacbc4989b3
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203508"
---
# <a name="colelinksdialog-class"></a>Klasa COleLinksDialog
Stosowane dla okna dialogowego OLE Edytuj łącza.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleLinksDialog : public COleDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleLinksDialog::COleLinksDialog](#colelinksdialog)|Konstruuje `COleLinksDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleLinksDialog::DoModal](#domodal)|Wyświetla okna dialogowego OLE Edytuj łącza.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleLinksDialog::m_el](#m_el)|Struktura typu OLEUIEDITLINKS kontrolujące zachowanie okna dialogowego.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz obiekt klasy `COleLinksDialog` umożliwia wywołanie tego okna dialogowego. Po `COleLinksDialog` obiekt został skonstruowany, możesz użyć [m_el](#m_el) strukturę, aby zainicjować wartości lub stany formantów w oknie dialogowym. `m_el` Struktury jest typu OLEUIEDITLINKS. Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcja elementu członkowskiego.  
  
> [!NOTE]
>  Kod kontenera generowane przez Kreatora aplikacji korzysta z tej klasy.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIEDITLINKS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuieditlinksa) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji dotyczących okien dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="domodal"></a>  COleLinksDialog::DoModal  
 Wyświetla okna dialogowego OLE Edytuj łącza.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jeden z następujących wartości:  
  
- IDOK, jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- IDCANCEL, jeśli użytkownik anulował okno dialogowe.  
  
- IDABORT, jeśli wystąpił błąd. Jeśli zwracana jest IDABORT, wywołaj `COleDialog::GetLastError` funkcja elementu członkowskiego, aby uzyskać więcej informacji o typie błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIEditLinks](/windows/desktop/api/oledlg/nf-oledlg-oleuieditlinksa) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Aby inicjowanie różne formanty okna dialogowego, ustawiając członkowie [m_el](#m_el) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po jest konstruowany obiektu okna dialogowego.  
  
##  <a name="colelinksdialog"></a>  COleLinksDialog::COleLinksDialog  
 Konstruuje `COleLinksDialog` obiektu.  
  
```  
COleLinksDialog (
    COleDocument* pDoc,  
    CView* pView,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pDoc*  
 Wskazuje dokument OLE, który zawiera łącza do edycji.  
  
 *pView*  
 Wskazuje bieżący widok na *pDoc*.  
  
 *Flagidw*  
 Flagi tworzenia zawiera 0 lub ELF_SHOWHELP, aby określić, czy przycisk Pomoc, będzie wyświetlane, gdy zostanie wyświetlone okno dialogowe.  
  
 *pParentWnd*  
 Wskazuje na obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne, okno dialogowe jest ustawiony na okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja tworzy tylko `COleLinksDialog` obiektu. Aby wyświetlić okno dialogowe, należy wywołać [DoModal](#domodal) funkcji.  
  
##  <a name="m_el"></a>  COleLinksDialog::m_el  
 Struktury typu OLEUIEDITLINKS używane do sterowania zachowaniem okno dialogowe Edytuj linki.  
  
```  
OLEUIEDITLINKS m_el;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie tej struktury można zmodyfikować bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIEDITLINKS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuieditlinksa) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
