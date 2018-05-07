---
title: Klasa COleCmdUI | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
dev_langs:
- C++
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e6195735c25bb188449638750f6100869a44f082
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="colecmdui-class"></a>Klasa COleCmdUI
Implementuje metodę MFC zaktualizować stan obiektów interfejsu użytkownika związane z `IOleCommandTarget`-driven funkcji aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleCmdUI : public CCmdUI  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleCmdUI::COleCmdUI](#colecmdui)|Konstruuje `COleCmdUI` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleCmdUI::Enable](#enable)|Ustawia lub usuwa flagę polecenia enable.|  
|[COleCmdUI::SetCheck](#setcheck)|Ustawia stan przełącznika/Wyłącz polecenia.|  
|[COleCmdUI::SetText](#settext)|Zwraca ciąg nazwy lub stan tekstu polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 W aplikacji, która nie jest włączona dla DocObjects, gdy użytkownik wyświetla menu w aplikacji MFC procesów **UPDATE_COMMAND_UI** powiadomień według. Każdy powiadomienia [CCmdUI](../../mfc/reference/ccmdui-class.md) obiekt, który można manipulować w celu odzwierciedlenia stanu określonego polecenia. Jednak po włączeniu aplikacji dla DocObjects przetwarza MFC **UPDATE_OLE_COMMAND_UI** powiadomień i przypisuje `COleCmdUI` obiektów.  
  
 `COleCmdUI` Umożliwia DocObject do odbierania poleceń, które pochodzą z jego kontenera interfejsu użytkownika (na przykład nowy plik, Otwórz, drukowania i tak dalej) i pozwala kontener służący do odbierania poleceń, które pochodzą z DocObject interfejsu użytkownika. Mimo że `IDispatch` może służyć do wysyłania tych samych poleceń `IOleCommandTarget` zapewnia prostszy sposób wykonywania zapytań i wykonać operacji, ponieważ zależy od standardowy zestaw poleceń, zazwyczaj bez argumentów, a uczestniczy bez informacji o typach. `COleCmdUI` można włączyć, zaktualizowania i ustawić inne właściwości polecenia interfejsu użytkownika DocObject. Do wywołania polecenia, należy wywołać [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).  
  
 Aby uzyskać więcej informacji o DocObjects zobacz [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) i [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md). Zobacz też [pierwsze kroki Internet: dokumenty aktywne](../../mfc/active-documents-on-the-internet.md) i [dokumenty aktywne](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [Ccmdui —](../../mfc/reference/ccmdui-class.md)  
  
 `COleCmdUI`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdocobj.h  
  
##  <a name="colecmdui"></a>  COleCmdUI::COleCmdUI  
 Konstruuje `COleCmdUI` obiekt skojarzony z poleceniem konkretnego interfejsu użytkownika.  
  
```  
COleCmdUI(
    OLECMD* rgCmds,  
    ULONG cCmds,  
    const GUID* m_pGroup);
```  
  
### <a name="parameters"></a>Parametry  
 `rgCmds`  
 Listę obsługiwanych poleceń skojarzone z danym identyfikatorem GUID. **OLECMD** struktury kojarzy poleceń z flagami polecenia.  
  
 *cCmds*  
 Liczba poleceń w `rgCmds`.  
  
 `pGroup`  
 Wskaźnik do identyfikatora GUID, który identyfikuje zestaw poleceń.  
  
### <a name="remarks"></a>Uwagi  
 `COleCmdUI` Obiektu zapewnia interfejs programistyczny aktualizowanie obiektów interfejsu użytkownika DocObject, takich jak elementy menu lub przycisków pasek sterowania. Obiekty interfejsu użytkownika można być włączone, wyłączone, zaznaczone i/lub wyczyszczone za pośrednictwem `COleCmdUI` obiektu.  
  
##  <a name="enable"></a>  COleCmdUI::Enable  
 Wywołanie tej funkcji, aby ustawić flagę polecenia `COleCmdUI` do obiektu **OLECOMDF_ENABLED**, który informuje interfejsu polecenie jest dostępna i włączona, lub Wyczyść flagę polecenia.  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>Parametry  
 `bOn`  
 Wskazuje, czy polecenie skojarzone z `COleCmdUI` obiektu powinny być włączone lub wyłączone. NonZero włącza polecenie; 0 wyłącza polecenie.  
  
##  <a name="setcheck"></a>  COleCmdUI::SetCheck  
 Wywołanie tej funkcji można ustawić stanu przełącznika/Wyłącz polecenia.  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nCheck`  
 Określanie stanu można ustawić lub wyłącza przełączanie wartość polecenia. Dostępne są następujące wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**1**|Ustawia na polecenie.|  
|**2**|Ustawia polecenie nieokreślony; Nie można określić stanu, ponieważ ten atrybut to polecenie jest zarówno i wyłączanie stanów w wyborze odpowiednich.|  
|Dowolna inna wartość|Ustawia polecenia wyłączone.|  
  
##  <a name="settext"></a>  COleCmdUI::SetText  
 Wywołanie tej funkcji, aby zwrócić nazwę lub stan ciąg tekstowy dla polecenia.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Wskaźnik do tekst, który ma być używany z poleceniem.  
  
## <a name="see-also"></a>Zobacz też  
 [Ccmdui — klasa](../../mfc/reference/ccmdui-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



