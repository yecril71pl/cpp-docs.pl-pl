---
title: Klasa COleUpdateDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleUpdateDialog
- AFXODLGS/COleUpdateDialog
- AFXODLGS/COleUpdateDialog::COleUpdateDialog
- AFXODLGS/COleUpdateDialog::DoModal
dev_langs:
- C++
helpviewer_keywords:
- COleUpdateDialog [MFC], COleUpdateDialog
- COleUpdateDialog [MFC], DoModal
ms.assetid: 699ca980-52b1-4cf8-9ab1-ac6767ad5b0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54088de4c07f1c58656aad468160ef58f0e41398
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="coleupdatedialog-class"></a>Klasa COleUpdateDialog
Używane dla przypadków specjalnych okna dialogowego OLE Edytuj łącza, który powinien być używany podczas należy zaktualizować tylko istniejące połączone lub obiekty osadzone w dokumencie.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleUpdateDialog : public COleLinksDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleUpdateDialog::COleUpdateDialog](#coleupdatedialog)|Konstruuje `COleUpdateDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleUpdateDialog::DoModal](#domodal)|Wyświetla **Edytuj łącza** okno dialogowe w trybie aktualizacji.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji dotyczących okien dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)  
  
 `COleUpdateDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="coleupdatedialog"></a>  COleUpdateDialog::COleUpdateDialog  
 Konstruuje `COleUpdateDialog` obiektu.  
  
```  
explicit COleUpdateDialog(
    COleDocument* pDoc,  
    BOOL bUpdateLinks = TRUE,  
    BOOL bUpdateEmbeddings = FALSE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDoc`  
 Wskazuje dokument zawierający łącza, które mogą wymagać aktualizacji.  
  
 *bUpdateLinks*  
 Flaga określająca, czy mają być aktualizowane powiązane obiekty.  
  
 *bUpdateEmbeddings*  
 Flaga określająca, czy mają być aktualizowane osadzonych obiektów.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okno nadrzędne okna dialogowego zostanie ustawiona do okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja tworzy tylko `COleUpdateDialog` obiektu. Aby wyświetlić okno dialogowe, wywołaj [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Ta klasa powinna być używana zamiast `COleLinksDialog` Aby zaktualizować tylko istniejące połączone lub osadzone elementy.  
  
##  <a name="domodal"></a>  COleUpdateDialog::DoModal  
 Wyświetla okna dialogowego Edytowanie łączy w tryb aktualizacji.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:  
  
- **IDOK** Jeśli okno dialogowe zwrócona pomyślnie.  
  
- **IDCANCEL** Jeśli żaden z elementów połączonego lub osadzonego w bieżącym dokumencie wymagają aktualizacji.  
  
- **IDABORT** Jeśli wystąpił błąd. Jeśli **IDABORT** jest zwracany, wywołaj [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcji członkowskiej, aby uzyskać więcej informacji o typie wystąpił błąd. Aby uzyskać listę możliwych błędów, zobacz [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie linki i/lub osadzeń są aktualizowane, chyba że użytkownik wybierze przycisk Anuluj.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC OCLIENT](../../visual-cpp-samples.md)   
 [Klasa COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)
