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
ms.openlocfilehash: fc5d51bfeb18b51be5a54c51046e3cd420fb1cb8
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852110"
---
# <a name="coleupdatedialog-class"></a>Klasa COleUpdateDialog
Stosowane w wyjątkowym przypadku okna dialogowego OLE Edytuj łącza, który powinien być używany gdy musisz zaktualizować jedynie istniejące połączone lub obiekty osadzone w dokumencie.  
  
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
|[COleUpdateDialog::DoModal](#domodal)|Wyświetla **Edytuj linki** okno dialogowe w trybie aktualizacji.|  
  
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
 *pDoc*  
 Wskazuje dokument zawierający linki, które mogą wymagać aktualizacji.  
  
 *bUpdateLinks*  
 Flaga określająca, czy połączone obiekty mają zostać uaktualnione.  
  
 *bUpdateEmbeddings*  
 Flaga określająca, czy mają zostać uaktualnione osadzonych obiektów.  
  
 *pParentWnd*  
 Wskazuje na obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do którego należy obiekt okna dialogowego. Jeśli ma wartość NULL, okno nadrzędne, okno dialogowe zostanie ustawiona do okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja tworzy tylko `COleUpdateDialog` obiektu. Aby wyświetlić okno dialogowe, należy wywołać [DoModal](../../mfc/reference/colelinksdialog-class.md#domodal). Ta klasa powinna być używana zamiast `COleLinksDialog` kiedy chcesz zaktualizować jedynie istniejące powiązane lub osadzonych elementów.  
  
##  <a name="domodal"></a>  COleUpdateDialog::DoModal  
 Wyświetla okno dialogowe Edytuj linki w tryb aktualizacji.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jeden z następujących wartości:  
  
- IDOK, jeśli okno dialogowe zwrócona pomyślnie.  
  
- IDCANCEL, jeśli żaden z elementów osadzony lub połączony w bieżącym dokumencie wymagają aktualizacji.  
  
- IDABORT, jeśli wystąpił błąd. Jeśli zwracana jest IDABORT, wywołaj [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) funkcja elementu członkowskiego, aby uzyskać więcej informacji o typie błędu, który wystąpił. Aby uzyskać listę możliwych błędów, zobacz [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie łącza i/lub osadzenia są aktualizowane, chyba że użytkownik wybierze przycisk Anuluj.  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC OCLIENT](../../visual-cpp-samples.md)   
 [Klasa COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)
