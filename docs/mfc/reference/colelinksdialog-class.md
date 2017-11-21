---
title: Klasa COleLinksDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleLinksDialog
- AFXODLGS/COleLinksDialog
- AFXODLGS/COleLinksDialog::COleLinksDialog
- AFXODLGS/COleLinksDialog::DoModal
- AFXODLGS/COleLinksDialog::m_el
dev_langs: C++
helpviewer_keywords:
- COleLinksDialog [MFC], COleLinksDialog
- COleLinksDialog [MFC], DoModal
- COleLinksDialog [MFC], m_el
ms.assetid: fb2eb638-2809-46db-ac74-392a732affc7
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be6c812864c6b5284b8db27d212ce82f8307e70c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="colelinksdialog-class"></a>Klasa COleLinksDialog
Używane dla okna dialogowego OLE Edytuj łącza.  
  
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
|[COleLinksDialog::DoModal](#domodal)|Wyświetla okno dialogowe OLE Edytuj łącza.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleLinksDialog::m_el](#m_el)|Struktura typu **OLEUIEDITLINKS** steruje zachowaniem okna dialogowego.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz obiekt klasy `COleLinksDialog` umożliwia wywołanie tego okna dialogowego. Po `COleLinksDialog` obiekt został skonstruowany, możesz użyć [m_el](#m_el) struktury zainicjować wartości lub stany formantów w oknie dialogowym. `m_el` Struktura jest typu **OLEUIEDITLINKS**. Aby uzyskać więcej informacji o korzystaniu z tej klasy okien dialogowych, zobacz [DoModal](#domodal) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Kod kontenera generowane przez Kreatora aplikacji korzysta z tej klasy.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) struktury w zestawie Windows SDK.  
  
 Aby uzyskać więcej informacji dotyczących okien dialogowych OLE specyficzne, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleLinksDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="domodal"></a>COleLinksDialog::DoModal  
 Wyświetla okno dialogowe OLE Edytuj łącza.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stan ukończenia dla okna dialogowego. Jedna z następujących wartości:  
  
- **IDOK** Jeśli pomyślnie zostało wyświetlone okno dialogowe.  
  
- **IDCANCEL** Jeśli użytkownik anulował okno dialogowe.  
  
- **IDABORT** Jeśli wystąpił błąd. Jeśli **IDABORT** jest zwracany, wywołaj `COleDialog::GetLastError` funkcji członkowskiej, aby uzyskać więcej informacji o typie wystąpił błąd. Aby uzyskać listę możliwych błędów, zobacz [OleUIEditLinks](http://msdn.microsoft.com/library/windows/desktop/ms679703) funkcji w zestawie Windows SDK.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli chcesz zainicjować różnych formantów okna dialogowego przez ustawienie członkami [m_el](#m_el) struktury, należy to zrobić przed wywołaniem `DoModal`, ale po konstruowania obiektu okna dialogowego.  
  
##  <a name="colelinksdialog"></a>COleLinksDialog::COleLinksDialog  
 Konstruuje `COleLinksDialog` obiektu.  
  
```  
COleLinksDialog (
    COleDocument* pDoc,  
    CView* pView,  
    DWORD dwFlags = 0,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pDoc`  
 Wskazuje dokumentu OLE, który zawiera łącza do edycji.  
  
 `pView`  
 Wskazuje bieżący widok na `pDoc`.  
  
 `dwFlags`  
 Tworzenie flagę zawiera albo 0 lub **ELF_SHOWHELP** do określenia, czy przycisk Pomoc, będzie wyświetlana, gdy zostanie wyświetlone okno dialogowe.  
  
 `pParentWnd`  
 Wskazuje obiekt okna nadrzędnego lub właściciela (typu `CWnd`) do której należy obiektu okna dialogowego. Jeśli jest **NULL**, okno nadrzędne, okno dialogowe ma ustawioną wartość okna głównego aplikacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja tworzy tylko `COleLinksDialog` obiektu. Aby wyświetlić okno dialogowe, wywołaj [DoModal](#domodal) funkcji.  
  
##  <a name="m_el"></a>COleLinksDialog::m_el  
 Struktura typu **OLEUIEDITLINKS** służące do sterowania zachowaniem okna dialogowego Edytowanie łączy.  
  
```  
OLEUIEDITLINKS m_el;  
```  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie tej konstrukcji może być modyfikowany bezpośrednio lub za pośrednictwem funkcji elementów członkowskich.  
  
 Aby uzyskać więcej informacji, zobacz [OLEUIEDITLINKS](http://msdn.microsoft.com/library/windows/desktop/ms678492) struktury w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)
