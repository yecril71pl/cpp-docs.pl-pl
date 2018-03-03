---
title: Klasa COlePropertiesDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
dev_langs:
- C++
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a5460926e1f58a557b26d8e5fa0a0ed763fc5de6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="colepropertiesdialog-class"></a>Klasa COlePropertiesDialog
Hermetyzuje okno dialogowe właściwości obiektów OLE wspólne systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COlePropertiesDialog : public COleDialog  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Konstruuje `COlePropertiesDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COlePropertiesDialog::DoModal](#domodal)|Wyświetla okno dialogowe i umożliwia użytkownikowi dokonanie wyboru.|  
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Wywoływane przez platformę, gdy skalowanie element dokumentu został zmieniony.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COlePropertiesDialog::m_gp](#m_gp)|Struktury używane do zainicjowania strony "Ogólne" `COlePropertiesDialog` obiektu.|  
|[COlePropertiesDialog::m_lp](#m_lp)|Struktura używaną do inicjalizacji na stronie "Link" `COlePropertiesDialog` obiektu.|  
|[COlePropertiesDialog::m_op](#m_op)|Używany do inicjowania struktury `COlePropertiesDialog` obiektu.|  
|[COlePropertiesDialog::m_psh](#m_psh)|Struktura służy do dodawania dodatkowych niestandardowe strony właściwości.|  
|[COlePropertiesDialog::m_vp](#m_vp)|Struktury używane w celu dostosowania strony "Widok" `COlePropertiesDialog` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Wspólne okna dialogowe właściwości obiektów OLE umożliwiają łatwe do wyświetlanie i modyfikowanie właściwości elementu dokumentu OLE w sposób zgodny ze standardami systemu Windows. Te właściwości obejmują między innymi informacje o pliku reprezentowanego przez element dokumentu, opcje wyświetlania ikonę i skalowanie obrazów i informacje na łącze do elementu (jeśli jest połączony element).  
  
 Aby użyć `COlePropertiesDialog` obiektów, najpierw utwórz obiekt przy użyciu `COlePropertiesDialog` konstruktora. Po skonstruowaniu okno dialogowe, wywołaj `DoModal` funkcji członkowskiej, aby wyświetlić okno dialogowe i Zezwalaj użytkownikowi na modyfikowanie właściwości elementu. `DoModal`Zwraca czy użytkownik wybrał OK ( **IDOK**) lub Anuluj ( **IDCANCEL**) przycisku. Oprócz przycisku OK i Anuluj znajduje się przycisk Zastosuj. Po wybraniu Zastosuj wszelkie zmiany wprowadzone do właściwości elementu dokumentu są stosowane do elementu i jego obrazu zostanie automatycznie zaktualizowana, ale pozostaje aktywna.  
  
 [M_psh](#m_psh) elementu członkowskiego danych jest wskaźnikiem do **PROPSHEETHEADER** struktury i w większości przypadków, nie musisz jawnie do niego dostęp. Jedynym wyjątkiem jest, gdy potrzebne są dodatkowe strony właściwości innych niż domyślne strony Ogólne, widok i łącza. W takim przypadku można zmodyfikować `m_psh` element członkowski danych do uwzględnienia stronach niestandardowych przed wywołaniem `DoModal` funkcję elementu członkowskiego.  
  
 Aby uzyskać więcej informacji dotyczących okien dialogowych OLE, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cdialog —](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog  
 Tworzy `COlePropertiesDialog` obiektu.  
  
```  
COlePropertiesDialog(
    COleClientItem* pItem,  
    UINT nScaleMin = 10,  
    UINT nScaleMax = 500,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskaźnik do elementu dokument, którego właściwości są używane.  
  
 *nScaleMin*  
 Minimalny procent dla obrazu elementu dokumentu skalowania.  
  
 *nScaleMax*  
 Maksymalny procent dla obrazu elementu dokumentu skalowania.  
  
 `pParentWnd`  
 Wskaźnik do nadrzędnego okna dialogowego lub właściciela.  
  
### <a name="remarks"></a>Uwagi  
 Klasy wspólnych okien dialogowych właściwości obiektów OLE z pochodzi `COlePropertiesDialog` w celu wdrożenia skalowania dla elementów dokumentu. Wszystkie okna dialogowe zaimplementowana przez wystąpienie tej klasy nie obsługuje skalowania elementu dokumentu.  
  
 Domyślnie okno dialogowe właściwości obiektów OLE typowe ma trzy domyślne strony:  
  
-   Ogólne  
  
     Ta strona zawiera informacje o systemie dla pliku reprezentowany przez element wybrany dokument. Na tej stronie użytkownika można przekonwertować wybranego elementu do innego typu.  
  
-   Widok  
  
     Ta strona zawiera opcje wyświetlania elementu, Zmiana ikony oraz zmienianie skalowanie obrazu.  
  
-   Łącze  
  
     Ta strona zawiera opcje zmiany lokalizacji połączonego elementu i aktualizowanie połączonego elementu. Na tej stronie użytkownik może przerwać łącze wybranego elementu.  
  
 Aby dodać strony poza tymi, które domyślnie dostępne, zmodyfikuj [m_psh](#m_psh) zmiennej członkowskiej przed zamknięciem konstruktora z `COlePropertiesDialog`-pochodnej klasy. Jest to implementacja zaawansowane `COlePropertiesDialog` konstruktora.  
  
##  <a name="domodal"></a>COlePropertiesDialog::DoModal  
 Wywołanie tej funkcji Członkowskich, aby wyświetlić okno dialogowe właściwości obiektów OLE wspólne systemu Windows i Zezwalaj użytkownikom na wyświetlanie i/lub zmienić różne właściwości element dokumentu.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **IDOK** lub **IDCANCEL** przypadku powodzenia; w przeciwnym razie wartość 0. **IDOK** i **IDCANCEL** są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.  
  
 Jeśli **IDCANCEL** jest zwracany, należy wywołać systemu Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkcji, aby ustalić, czy wystąpił błąd.  
  
##  <a name="m_gp"></a>COlePropertiesDialog::m_gp  
 Struktura typu [OLEUIGNRLPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687297)używane do zainicjowania strony Ogólne okna dialogowego właściwości obiektu OLE.  
  
```  
OLEUIGNRLPROPS m_gp;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta strona zawiera typ i rozmiar osadzenia i zezwala użytkownikowi na dostęp do okna dialogowego Convert. Ta strona zawiera również link docelowy Jeśli obiekt jest łącze.  
  
 Aby uzyskać więcej informacji na temat **OLEUIGNRLPROPS** struktury, zobacz zestaw Windows SDK.  
  
##  <a name="m_lp"></a>COlePropertiesDialog::m_lp  
 Struktura typu [OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735)używane do zainicjowania łącza strony okna dialogowego właściwości obiektu OLE.  
  
```  
OLEUILINKPROPS m_lp;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta strona zawiera lokalizację połączonego elementu i umożliwia użytkownikowi aktualizacji lub przerwać łącze do elementu.  
  
 Aby uzyskać więcej informacji na temat **OLEUILINKPROPS** struktury, zobacz zestaw Windows SDK.  
  
##  <a name="m_op"></a>COlePropertiesDialog::m_op  
 Struktura typu [OLEUIOBJECTPROPS](http://msdn.microsoft.com/library/windows/desktop/ms687199), używana zainicjować okno dialogowe właściwości obiektów OLE wspólnej.  
  
```  
OLEUIOBJECTPROPS m_op;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta struktura zawiera elementy członkowskie używany do inicjowania strony Ogólne, łączy i widoku.  
  
 Aby uzyskać więcej informacji, zobacz **OLEUIOBJECTPROPS** i [OLEUILINKPROPS](http://msdn.microsoft.com/library/windows/desktop/ms680735) struktury w zestawie Windows SDK.  
  
##  <a name="m_psh"></a>COlePropertiesDialog::m_psh  
 Struktura typu [PROPSHEETHEADER](http://msdn.microsoft.com/library/windows/desktop/bb774546), której członkowie przechowywania właściwości obiektu okna dialogowego.  
  
```  
PROPSHEETHEADER m_psh;  
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowania `COlePropertiesDialog` obiektu, można użyć `m_psh` można ustawić różne aspekty okna dialogowego przed wywołaniem `DoModal` funkcję elementu członkowskiego.  
  
 Jeśli zmodyfikujesz `m_psh` element członkowski danych bezpośrednio, spowoduje zastąpienie wszelkich zachowanie domyślne.  
  
 Aby uzyskać więcej informacji na temat **PROPSHEETHEADER** struktury, zobacz zestaw Windows SDK.  
  
##  <a name="m_vp"></a>COlePropertiesDialog::m_vp  
 Struktura typu [OLEUIVIEWPROPS](http://msdn.microsoft.com/library/windows/desktop/ms693751)używane do zainicjowania strony widoku okna dialogowego właściwości obiektu OLE.  
  
```  
OLEUIVIEWPROPS m_vp;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta strona umożliwia użytkownikowi przełączanie się między "zawartość" i "odpowiednikiem" widoki obiektu i zmienić jej skalowanie w kontenerze. Również umożliwia użytkownikowi dostęp do okna dialogowego Zmień ikonę, gdy obiekt jest wyświetlany w postaci ikony.  
  
 Aby uzyskać więcej informacji na temat **OLEUIVIEWPROPS** struktury, zobacz zestaw Windows SDK.  
  
##  <a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale  
 Wywoływane przez platformę, gdy zmieniono wartość skalowania i wybrano OK lub Zastosuj.  
  
```  
virtual BOOL OnApplyScale(
    COleClientItem* pItem,  
    int nCurrentScale,  
    BOOL bRelativeToOrig);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Wskaźnik do elementu dokument, którego właściwości są używane.  
  
 `nCurrentScale`  
 Liczbowa wartość skalowania okna dialogowego.  
  
 *bRelativeToOrig*  
 Wskazuje, czy skalowanie stosuje się do oryginalnego rozmiaru element dokumentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obsługiwane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nie działa. Konieczne jest przesłonięcie tej funkcji, aby włączyć formanty skalowania.  
  
> [!NOTE]
>  Przed wyświetleniem wspólne okno dialogowe właściwości obiektu OLE, struktura wywołuje tę funkcję z **NULL** dla `pItem` i 1 dla `nCurrentScale`. Jest to realizowane ustalenie skalowania kontrolki powinno być włączone.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC OK](../../visual-cpp-samples.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Klasa CPropertyPage](../../mfc/reference/cpropertypage-class.md)
