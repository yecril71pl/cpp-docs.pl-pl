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
ms.openlocfilehash: 9b057620e0ea348559b9c37f55ba7658b7f5270c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851486"
---
# <a name="colecmdui-class"></a>Klasa COleCmdUI
Implementuje metodę dla MFC zaktualizować stan obiektów interfejsu użytkownika związane z `IOleCommandTarget`-driven funkcje aplikacji.  
  
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
|[COleCmdUI::Enable](#enable)|Ustawia lub czyści flagi polecenie Włącz.|  
|[COleCmdUI::SetCheck](#setcheck)|Ustawia stan wł. / wył. przełącznik polecenia.|  
|[COleCmdUI::SetText](#settext)|Zwraca nazwę lub stan ciąg tekstowy dla polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 W aplikacji, który nie włączono DocObjects, kiedy widoki użytkowników w menu w aplikacji MFC przetwarza UPDATE_COMMAND_UI powiadomień według. Każdego powiadomienia [CCmdUI](../../mfc/reference/ccmdui-class.md) obiekt, który można manipulować w celu odzwierciedlenia stanu określonego polecenia. Jednak jeśli aplikacja została włączona dla DocObjects, MFC przetwarza UPDATE_OLE_COMMAND_UI powiadomienia i przypisuje `COleCmdUI` obiektów.  
  
 `COleCmdUI` zezwala na DocObject w celu odbierania poleceń, które pochodzą z jego kontenerem interfejsu użytkownika (na przykład nowy plik, Otwórz, drukowania i tak dalej) i umożliwia kontenera w celu odbierania poleceń, które pochodzą z interfejsu użytkownika DocObject. Mimo że `IDispatch` może służyć do wysyłania tych samych poleceń `IOleCommandTarget` zapewnia prostszy sposób wykonywania zapytań i wykonać operacji, ponieważ opiera się na zestaw standardowych poleceń, zwykle bez argumentów, i jest używana nie informacji o typie. `COleCmdUI` można włączyć, aktualizowanie i ustawić inne właściwości polecenia interfejsu użytkownika DocObject. Jeśli chcesz wywołać polecenie wywołania [COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).  
  
 Aby uzyskać więcej informacji na temat DocObjects zobacz [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) i [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md). Zobacz też [Internet pierwszych kroków: dokumenty aktywne](../../mfc/active-documents-on-the-internet.md) i [dokumenty aktywne](../../mfc/active-documents-on-the-internet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CCmdUI](../../mfc/reference/ccmdui-class.md)  
  
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
 *rgCmds*  
 Listę obsługiwanych poleceń skojarzone z danym identyfikatorem GUID. `OLECMD` Struktury kojarzy poleceń przy użyciu flag poleceń.  
  
 *cCmds*  
 Liczba poleceń w *rgCmds*.  
  
 *pGroup*  
 Wskaźnik na identyfikator GUID, który identyfikuje zestaw poleceń.  
  
### <a name="remarks"></a>Uwagi  
 `COleCmdUI` Obiekt zapewnia interfejs programistyczny dla aktualizowanie obiektów interfejsu użytkownika DocObject, np. w menu i przycisków paska sterowania. Obiekty interfejsu użytkownika może być włączone, wyłączone, zaznaczone i/lub wyczyszczone za pośrednictwem `COleCmdUI` obiektu.  
  
##  <a name="enable"></a>  COleCmdUI::Enable  
 Wywołaj tę funkcję, należy ustawić flagę polecenia `COleCmdUI` obiektu OLECOMDF_ENABLED, która informuje o tym interfejsie polecenie jest dostępna i włączona, lub Wyczyść flagę polecenia.  
  
```  
virtual void Enable(BOOL bOn);
```  
  
### <a name="parameters"></a>Parametry  
 *bOn*  
 Wskazuje, czy polecenie skojarzone z `COleCmdUI` obiektów, które powinny być włączone lub wyłączone. NonZero umożliwia polecenie. 0 wyłącza polecenie.  
  
##  <a name="setcheck"></a>  COleCmdUI::SetCheck  
 Wywołaj tę funkcję, aby ustawić stan włączenia/wyłączenia Przełącz polecenia.  
  
```  
virtual void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 *nSprawdź*  
 Wartość określająca stan używany do ustawiania wł. / wył. przełącznik polecenia. Dostępne są następujące wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|**1**|Ustawia na polecenia.|  
|**2**|Ustawia polecenia nieokreślony; Nie można ustalić stanu, ponieważ atrybut tego polecenia jest zarówno i wyłączanie stanów w odpowiedni wybór.|  
|Dowolna inna wartość|Określa polecenie, aby wyłączyć.|  
  
##  <a name="settext"></a>  COleCmdUI::SetText  
 Wywołaj tę funkcję, aby zwrócić nazwę lub stan ciąg tekstowy dla polecenia.  
  
```  
virtual void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszText*  
 Wskaźnik na tekst, który ma być używany z poleceniem.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CCmdUI](../../mfc/reference/ccmdui-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



