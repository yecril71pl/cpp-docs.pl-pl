---
title: Klasa COlePropertiesDialog | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c44abc596f5338ad82b49bc9761abfc5bb26a1a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216205"
---
# <a name="colepropertiesdialog-class"></a>Klasa COlePropertiesDialog
Hermetyzuje wspólne okno dialogowe właściwości obiektu OLE Windows.  
  
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
|[COlePropertiesDialog::DoModal](#domodal)|Zostanie wyświetlone okno dialogowe i umożliwia użytkownikowi dokonać wyboru.|  
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Wywoływane przez platformę, gdy skalowanie element dokumentu został zmieniony.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COlePropertiesDialog::m_gp](#m_gp)|Struktury używane do zainicjowania strony "Ogólne" `COlePropertiesDialog` obiektu.|  
|[COlePropertiesDialog::m_lp](#m_lp)|Struktury używane do zainicjowania strony "Link" `COlePropertiesDialog` obiektu.|  
|[COlePropertiesDialog::m_op](#m_op)|Struktury używane do zainicjowania `COlePropertiesDialog` obiektu.|  
|[COlePropertiesDialog::m_psh](#m_psh)|Struktura służy do dodawania dodatkowych niestandardowe strony właściwości.|  
|[COlePropertiesDialog::m_vp](#m_vp)|Struktury używane w celu dostosowania strony "View" `COlePropertiesDialog` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Wspólne okna dialogowe właściwości obiektu OLE zapewniają prosty sposób wyświetlania i modyfikacji właściwości elementu dokumentu OLE w sposób zgodny ze standardami Windows. Te właściwości obejmują między innymi informacje o pliku, reprezentowane przez element dokumentu, opcje wyświetlania ikon i skalowanie obrazów oraz informacje na łącze do elementu (jeśli jest połączony element).  
  
 Aby użyć `COlePropertiesDialog` obiektów, najpierw utwórz obiekt przy użyciu `COlePropertiesDialog` konstruktora. Po został skonstruowany okno dialogowe, wywołania `DoModal` funkcja elementu członkowskiego, aby wyświetlić okno dialogowe i umożliwia użytkownikowi modyfikowanie właściwości elementu. `DoModal` Zwraca, czy użytkownik wybrał przycisk anulowania (IDCANCEL) lub OK (IDOK). Oprócz przyciskami OK i Anuluj ma przycisk Zastosuj. Po wybraniu Zastosuj wszelkie zmiany wprowadzone do właściwości elementu dokumentu są stosowane do elementu, a obraz jest automatycznie aktualizowana, ale pozostaje aktywna.  
  
 [M_psh](#m_psh) element członkowski danych jest wskaźnikiem do `PROPSHEETHEADER` struktury i w większości przypadków nie musisz jawnie do niego dostęp. Jedynym wyjątkiem jest, gdy będą potrzebne dodatkowe strony właściwości poza domyślne strony Ogólne, widok i łącza. W takim przypadku można zmodyfikować `m_psh` element członkowski danych do uwzględnienia Twoich stron niestandardowych przed wywołaniem `DoModal` funkcja elementu członkowskiego.  
  
 Aby uzyskać więcej informacji dotyczących okien dialogowych OLE, zobacz artykuł [okna dialogowe w OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COlePropertiesDialog`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxodlgs.h  
  
##  <a name="colepropertiesdialog"></a>  COlePropertiesDialog::COlePropertiesDialog  
 Tworzy `COlePropertiesDialog` obiektu.  
  
```  
COlePropertiesDialog(
    COleClientItem* pItem,  
    UINT nScaleMin = 10,  
    UINT nScaleMax = 500,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pItem*  
 Wskaźnik do elementu dokumentu, którego właściwości są używane.  
  
 *nScaleMin*  
 Minimalny procent dla obrazu elementu dokumentu skalowania.  
  
 *nScaleMax*  
 Maksymalny procent dla obrazu elementu dokumentu skalowania.  
  
 *pParentWnd*  
 Wskaźnik do nadrzędnej lub właściciela okno dialogowe.  
  
### <a name="remarks"></a>Uwagi  
 Pochodzi z klasy wspólnych okien dialogowych właściwości obiektu OLE z `COlePropertiesDialog` w celu wdrożenia, skalowania elementów dokumentu. Wszystkie okna dialogowe implementowany przez wystąpienie tej klasy nie obsługuje skalowania element dokumentu.  
  
 Domyślnie przez wspólne okno dialogowe właściwości obiektu OLE ma trzy strony domyślnej:  
  
-   Ogólne  
  
     Ta strona zawiera informacje o systemie dla pliku, reprezentowane przez element wybrany dokument. Na tej stronie użytkownika można przekonwertować wybrany element do innego typu.  
  
-   Widok  
  
     Ta strona zawiera opcje wyświetlania elementu, Zmiana ikony i zmienianie skalowania obrazu.  
  
-   Łącze  
  
     Ta strona zawiera opcje dotyczące zmiany lokalizacji połączony element i aktualizowanie połączonego elementu. Z tej strony użytkownik może przerwać łącze wybranego elementu.  
  
 Aby dodać strony poza tymi, które domyślnie dostępne, należy zmodyfikować [m_psh](#m_psh) zmiennej składowej przed opuszczeniem konstruktora obiektu usługi `COlePropertiesDialog`-klasy pochodnej. Jest to zaawansowana implementacja `COlePropertiesDialog` konstruktora.  
  
##  <a name="domodal"></a>  COlePropertiesDialog::DoModal  
 Wywołaj tę funkcję elementu członkowskiego, aby wyświetlić wspólne okno dialogowe właściwości obiektu OLE Windows i umożliwia użytkownikowi wyświetlanie i/lub zmienić różne właściwości element dokumentu.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 IDOK lub IDCANCEL, jeśli to się powiedzie; w przeciwnym razie 0. IDOK i IDCANCEL są stałe, które wskazują, czy użytkownik wybrał przycisk OK, lub przycisk Anuluj.  
  
 Jeśli zwracana jest IDCANCEL, można wywołać Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkcję, aby ustalić, czy wystąpił błąd.  
  
##  <a name="m_gp"></a>  COlePropertiesDialog::m_gp  
 Struktury typu [OLEUIGNRLPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuignrlpropsa), który jest używany do zainicjowania strony Ogólne okna dialogowego właściwości obiektu OLE.  
  
```  
OLEUIGNRLPROPS m_gp;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta strona pokazuje typ i rozmiar osadzania i pozwala użytkownikowi na dostęp do okna dialogowego konwersji. Ta strona zawiera również miejsce docelowe łącza czy obiekt jest linkiem.  
  
 Aby uzyskać więcej informacji na temat `OLEUIGNRLPROPS` struktury, zobacz zestaw Windows SDK.  
  
##  <a name="m_lp"></a>  COlePropertiesDialog::m_lp  
 Struktury typu [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa), który jest używany do zainicjowania strony łącze okna dialogowego właściwości obiektu OLE.  
  
```  
OLEUILINKPROPS m_lp;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta strona pokazuje lokalizację połączony element i pozwala użytkownikowi na aktualizowanie lub przerwać łącze do elementu.  
  
 Aby uzyskać więcej informacji na temat `OLEUILINKPROPS` struktury, zobacz zestaw Windows SDK.  
  
##  <a name="m_op"></a>  COlePropertiesDialog::m_op  
 Struktury typu [OLEUIOBJECTPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiobjectpropsa), który jest używany do zainicjowania wspólne okno dialogowe właściwości obiektu OLE.  
  
```  
OLEUIOBJECTPROPS m_op;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta struktura zawiera elementy członkowskie, używane do zainicjowania ogólne, Link i widoku strony.  
  
 Aby uzyskać więcej informacji, zobacz OLEUIOBJECTPROPS i [OLEUILINKPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuilinkpropsa) struktur w zestawie Windows SDK.  
  
##  <a name="m_psh"></a>  COlePropertiesDialog::m_psh  
 Struktury typu [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2), której członkowie przechowywania właściwości obiektu okna dialogowego.  
  
```  
PROPSHEETHEADER m_psh;  
```  
  
### <a name="remarks"></a>Uwagi  
 Po konstruowanie `COlePropertiesDialog` obiektu, możesz użyć `m_psh` można ustawić różne aspekty okno dialogowe przed wywołaniem `DoModal` funkcja elementu członkowskiego.  
  
 Jeśli zmodyfikujesz `m_psh` element członkowski danych bezpośrednio, spowoduje zastąpienie wszelkich zachowanie domyślne.  
  
 Aby uzyskać więcej informacji na temat `PROPSHEETHEADER` struktury, zobacz zestaw Windows SDK.  
  
##  <a name="m_vp"></a>  COlePropertiesDialog::m_vp  
 Struktury typu [OLEUIVIEWPROPS](/windows/desktop/api/oledlg/ns-oledlg-tagoleuiviewpropsa), który jest używany do zainicjowania strony widoku okna dialogowego właściwości obiektu OLE.  
  
```  
OLEUIVIEWPROPS m_vp;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta strona umożliwia użytkownikowi przełączanie się między "treści" i "ikony" widoki obiektu i zmienić jej skalowanie w kontenerze. Umożliwia również użytkownikom dostęp do okna dialogowego Zmień ikonę po obiekcie są wyświetlane jako ikona.  
  
 Aby uzyskać więcej informacji na temat `OLEUIVIEWPROPS` struktury, zobacz zestaw Windows SDK.  
  
##  <a name="onapplyscale"></a>  COlePropertiesDialog::OnApplyScale  
 Wywoływane przez platformę, gdy zmieniono wartość skalowania i OK lub Zastosuj został wybrany.  
  
```  
virtual BOOL OnApplyScale(
    COleClientItem* pItem,  
    int nCurrentScale,  
    BOOL bRelativeToOrig);
```  
  
### <a name="parameters"></a>Parametry  
 *pItem*  
 Wskaźnik do elementu dokumentu, którego właściwości są używane.  
  
 *nCurrentScale*  
 Wartość liczbową o skali okna dialogowego.  
  
 *bRelativeToOrig*  
 Wskazuje, czy skalowanie mają zastosowanie do oryginalnego rozmiaru element dokumentu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli obsługiwane; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja nic nie robi. Musisz przesłonić tę funkcję, aby włączyć kontrolki skalowania.  
  
> [!NOTE]
>  Przed wyświetleniem wspólne okno dialogowe właściwości obiektu OLE, struktura wywołuje tę funkcję z wartość NULL w przypadku *pItem* i 1 dla *nCurrentScale*. W ten sposób ustalić skalowania kontrolki powinno być włączone.  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC OK](../../visual-cpp-samples.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDialog](../../mfc/reference/coledialog-class.md)   
 [Klasa CPropertyPage](../../mfc/reference/cpropertypage-class.md)
