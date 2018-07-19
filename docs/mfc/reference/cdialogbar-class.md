---
title: Klasa CDialogBar | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
dev_langs:
- C++
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ff69a4974cd85471b0cfa039f32ee0c1a76f82a
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336387"
---
# <a name="cdialogbar-class"></a>Klasa CDialogBar
Oferuje funkcje Windows niemodalnego okna dialogowego na pasku sterowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDialogBar : public CControlBar  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDialogBar::CDialogBar](#cdialogbar)|Konstruuje `CDialogBar` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDialogBar::Create](#create)|Tworzy Pasek dialogowy Windows i dołącza je do `CDialogBar` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Pasek dialogowy przypomina okno dialogowe, ponieważ zawiera standardowych kontrolek Windows, które użytkownik może karcie między. Inny podobieństwa jest utworzenie szablonu okna dialogowego do reprezentowania paska dialogowego.  
  
 Tworzenie i używanie paska dialogowego jest podobne do tworzenia i używania `CFormView` obiektu. Najpierw za pomocą [Edytor okien dialogowych](../../windows/dialog-editor.md) do definiowania szablonu okna dialogowego ze stylem WS_CHILD i nie inne stylu. Szablon nie może mieć styl WS_VISIBLE. W kodzie aplikacji należy wywołać konstruktora do konstruowania `CDialogBar` obiektu, a następnie wywołaj `Create` utworzyć okno Pasek dialogowy i dołącz ją do `CDialogBar` obiektu.  
  
 Aby uzyskać więcej informacji na temat `CDialogBar`, zapoznaj się z artykułem [paski dialogowe](../../mfc/dialog-bars.md) i [techniczne 31 Uwaga](../../mfc/tn031-control-bars.md), pasków sterowania.  
  
> [!NOTE]
>  W bieżącej wersji `CDialogBar` obiektu nie może obsługiwać kontrolek formularzy Windows Forms. Aby uzyskać więcej informacji na temat formantów formularzy Windows w języku Visual C++, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar  
 Konstruuje `CDialogBar` obiektu.  
  
```  
CDialogBar();
```  
  
##  <a name="create"></a>  CDialogBar::Create  
 Ładuje szablonu zasobów okno dialogowe, które są określone przez `lpszTemplateName` lub `nIDTemplate`, tworzy okno Pasek dialogowy, ustawia jego styl i kojarzy ją z `CDialogBar` obiektu.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    LPCTSTR lpszTemplateName,  
    UINT nStyle,  
    UINT nID);

 
virtual BOOL Create(
    CWnd* pParentWnd,  
    UINT nIDTemplate,  
    UINT nStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Wskaźnik do elementu nadrzędnego `CWnd` obiektu.  
  
 *lpszTemplateName*  
 Wskaźnik na nazwę `CDialogBar` obiektu szablonu zasobu okna dialogowego.  
  
 *nStyle*  
 Styl paska narzędzi. Style dodatkowych narzędzi, obsługiwane są następujące:  
  
- Pasek sterowania CBRS_TOP to u góry okna ramki.  
  
- Pasek sterowania CBRS_BOTTOM jest w dolnej części okna ramki.  
  
- Pasek sterowania CBRS_NOALIGN nie zostaje przeniesiony, gdy zmieniany jest rozmiar obiektu nadrzędnego.  
  
- Pasek sterowania CBRS_TOOLTIPS Wyświetla etykietek narzędzi.  
  
- Pasek sterowania CBRS_SIZE_DYNAMIC jest dynamiczny.  
  
- Pasek sterowania CBRS_SIZE_FIXED jest stała.  
  
- Pasek sterowania CBRS_FLOATING jest liczb zmiennoprzecinkowych.  
  
- Pasek stanu CBRS_FLYBY Wyświetla informacje o przycisku.  
  
- Pasek sterowania CBRS_HIDE_INPLACE są niewidoczne dla użytkownika.  
  
 *nID*  
 Identyfikator formantu paska dialogowego.  
  
 *nIDTemplate*  
 Identyfikator zasobu `CDialogBar` obiektu szablonu okna dialogowego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli określisz style wyrównania CBRS_TOP lub CBRS_BOTTOM, Pasek dialogowy się szerokość ramki okna i jego wysokość jest zasób określony przez *nIDTemplate*. Jeśli określisz style wyrównania CBRS_LEFT lub CBRS_RIGHT, wysokość paska dialogowego jest to, że ramki okna i jego szerokość jest zasób określony przez *nIDTemplate*.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Ccontrolbar — klasa](../../mfc/reference/ccontrolbar-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFormView](../../mfc/reference/cformview-class.md)   
 [Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
