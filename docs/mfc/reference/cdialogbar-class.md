---
title: Cdialogbar — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 7dbb2d8202e9b87d2825b7d40a0dde4323246aa0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366717"
---
# <a name="cdialogbar-class"></a>Cdialogbar — klasa
Udostępnia funkcje niemodalnego okna dialogowego systemu Windows w pasek sterowania.  
  
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
|[CDialogBar::Create](#create)|Tworzy Pasek dialogowy systemu Windows i dołącza go do `CDialogBar` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Okno dialogowe jest podobny do paska dialogowego zawierają formanty standardowe systemu Windows, które użytkownik może karcie między. Inny podobieństwa jest utworzenie szablonu okna dialogowego do reprezentowania paska dialogowego.  
  
 Tworzenie i używanie paska dialogowego jest podobny do tworzenia i używania `CFormView` obiektu. Najpierw użyj [Edytor okien dialogowych](../../windows/dialog-editor.md) do definiowania szablonu okna dialogowego przy użyciu stylu **ws_child —** i żaden inny styl. Szablon nie może mieć styl **ws_visible —**. W kodzie aplikacji należy wywołać konstruktora, aby utworzyć `CDialogBar` obiekt, a następnie wywołaj **Utwórz** Tworzenie okna paska dialogowego i dołączenie go do `CDialogBar` obiektu.  
  
 Aby uzyskać więcej informacji na temat `CDialogBar`, zapoznaj się z artykułem [paski dialogowe](../../mfc/dialog-bars.md) i [31 Uwaga techniczna](../../mfc/tn031-control-bars.md), paski sterowania.  
  
> [!NOTE]
>  W bieżącej wersji `CDialogBar` obiektu nie może obsługiwać formanty formularzy systemu Windows. Aby uzyskać więcej informacji na temat formanty formularzy systemu Windows w programie Visual C++, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar —](../../mfc/reference/ccontrolbar-class.md)  
  
 `CDialogBar`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxext.h  
  
##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar  
 Konstruuje `CDialogBar` obiektu.  
  
```  
CDialogBar();
```  
  
##  <a name="create"></a>  CDialogBar::Create  
 Ładuje okno dialogowe szablon zasobu określonego przez `lpszTemplateName` lub `nIDTemplate`, tworzy okno dialogowe pasek, ustawia jego styl i kojarzy ją z `CDialogBar` obiektu.  
  
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
 `pParentWnd`  
 Wskaźnik do elementu nadrzędnego `CWnd` obiektu.  
  
 `lpszTemplateName`  
 Wskaźnik do nazwy `CDialogBar` obiektu okno dialogowe zasobu szablon.  
  
 `nStyle`  
 Styl toolbar. Style dodatkowych narzędzi obsługiwane są następujące:  
  
- `CBRS_TOP` Pasek sterowania jest u góry okna ramki.  
  
- `CBRS_BOTTOM` Pasek sterowania jest w dolnej części okna ramki.  
  
- `CBRS_NOALIGN` Pasek sterowania nie zostaje przeniesiony, gdy zmieniany jest rozmiar obiektu nadrzędnego.  
  
- `CBRS_TOOLTIPS` Pasek sterowania Wyświetla etykietki narzędzi.  
  
- **Cbrs_size_dynamic —** pasek sterowania jest dynamiczny.  
  
- **Cbrs_size_fixed —** pasek sterowania został rozwiązany.  
  
- **CBRS_FLOATING** zmiennoprzecinkową jest pasek sterowania.  
  
- `CBRS_FLYBY` Pasek stanu wyświetla informacje o przycisku.  
  
- **CBRS_HIDE_INPLACE** pasek sterowania jest niewidoczny dla użytkownika.  
  
 `nID`  
 Identyfikator formantu paska dialogowego.  
  
 `nIDTemplate`  
 Identyfikator zasobu `CDialogBar` obiektu okno dialogowe szablonu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli określisz `CBRS_TOP` lub `CBRS_BOTTOM` styl wyrównanie szerokość paska dialogowego jest to, że ramka okna i jego wysokość jest zasobu określonego przez `nIDTemplate`. Jeśli określisz `CBRS_LEFT` lub `CBRS_RIGHT` styl wyrównanie wysokość paska dialogowego jest to, że ramka okna i szerokości, jest zasobu określonego przez `nIDTemplate`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Ccontrolbar — klasa](../../mfc/reference/ccontrolbar-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CFormView](../../mfc/reference/cformview-class.md)   
 [Klasa CControlBar](../../mfc/reference/ccontrolbar-class.md)
