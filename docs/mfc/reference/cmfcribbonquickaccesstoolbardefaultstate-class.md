---
title: Klasa CMFCRibbonQuickAccessToolBarDefaultState | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom
- AFXRIBBONQUICKACCESSTOOLBAR/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CMFCRibbonQuickAccessToolBarDefaultState
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], AddCommand
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], CopyFrom
- CMFCRibbonQuickAccessToolBarDefaultState [MFC], RemoveAll
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e60157ee70ea5df3835d817972a7bcb0dfe2db0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonquickaccesstoolbardefaultstate-class"></a>Klasa CMFCRibbonQuickAccessToolBarDefaultState
Klasa pomocy, która zarządza stan domyślny dla paska narzędzi Szybki dostęp, który znajduje się w pasku wstążki ( [CMFCRibbonBar klasy](../../mfc/reference/cmfcribbonbar-class.md)).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMFCRibbonQuickAccessToolBarDefaultState  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](#cmfcribbonquickaccesstoolbardefaultstate)|Konstruuje `CMFCRibbonQuickAccessToolbarDefaultState` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand)|Umożliwia dodanie polecenia do stanu domyślnego dla paska narzędzi Szybki dostęp. Nie zmienia się paska narzędzi.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](#copyfrom)|Kopiuje właściwości jednego paska narzędzi Szybki dostęp do innego.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](#removeall)|Usuwa wszystkie polecenia z paska narzędzi Szybki dostęp. Nie zmienia się paska narzędzi.|  
  
## <a name="remarks"></a>Uwagi  
 Po utworzeniu paska narzędzi Szybki dostęp do aplikacji, firma Microsoft zaleca ustawienie stanu domyślnego przez wywołanie metody [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate). Ten stan domyślny jest przywracany po kliknięciu **zresetować** znajdującego się na **Dostosuj** strony aplikacji **opcje** okno dialogowe.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób tworzenia obiektu `CMFCRibbonQuickAccessToolbarDefaultState` klasy i jak dodać polecenia do stanu domyślnego dla paska narzędzi Szybki dostęp.  
  
 [!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/cpp/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxribbonquickaccesstoolbar.h  
  
##  <a name="addcommand"></a>CMFCRibbonQuickAccessToolBarDefaultState::AddCommand  
 Umożliwia dodanie polecenia do stanu domyślnego dla paska narzędzi Szybki dostęp.  
  
```  
void AddCommand(
    UINT uiCmd,  
    BOOL bIsVisible=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] uiCmd`  
 Określa identyfikator polecenia.  
  
 `[in] bIsVisible`  
 Ustawia widoczność polecenia, gdy pasek narzędzi Szybki dostęp jest w stanie domyślnym.  
  
### <a name="remarks"></a>Uwagi  
 Dodawanie polecenia do CMFCRibbonQuickAccessToolBarDefaultState wykonuje trzech wyników. Najpierw każdego polecenia dodanego znajduje się na liście rozwijanej po prawej stronie paska narzędzi Szybki dostęp. W ten sposób użytkownika można łatwo dodawać i usuwać tego polecenia z paska narzędzi Szybki dostęp. Po drugie, paska narzędzi Szybki dostęp jest resetowany do wyświetlenia tylko tych poleceń, które są wyświetlane jako widoczna w stanie domyślnym po kliknięciu przez użytkownika **resetowania** przycisk **Dostosuj** okno dialogowe. Trzeci, jeśli nie wywołano [CMFCRibbonBar::SetQuickAccessCommands](../../mfc/reference/cmfcribbonbar-class.md#setquickaccesscommands), paska narzędzi Szybki dostęp używa widocznych poleceń z tej listy jako domyślne polecenia widoczny przy pierwszym uruchomieniu aplikacji użytkownika. Po dodaniu wszystkich poleceń, które chcesz wywołać [CMFCRibbonBar::SetQuickAccessDefaultState](../../mfc/reference/cmfcribbonbar-class.md#setquickaccessdefaultstate) można ustawić tego wystąpienia jako domyślny stan dla paska szybkiego dostępu ten pasek wstążki.  
  
##  <a name="copyfrom"></a>CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom  
 Kopiuje właściwości jednego paska narzędzi Szybki dostęp do innego.  
  
```  
void CopyFrom(const CMFCRibbonQuickAccessToolBarDefaultState& src);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`src`  
 Odwołanie do źródła `CMFCRibbonQuickAccessToolBarDefaultState` obiektu do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia skopiowanie każdego polecenia ze źródła `CMFCRibbonQuickAccessToolBarDefaultState` obiektu do tego obiektu przy użyciu [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) metody.  
  
##  <a name="cmfcribbonquickaccesstoolbardefaultstate"></a>CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState  
 Tworzy pasek narzędzi Szybki dostęp do domyślnego stanu obiektu.  
  
```  
CMFCRibbonQuickAccessToolBarDefaultState();
```  
  
### <a name="remarks"></a>Uwagi  
 Domyślnie listę poleceń, które nowe wystąpienie klasy [CMFRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md) zawiera jest pusta.  
  
##  <a name="removeall"></a>CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll  
 Czyści listę poleceń domyślne paska narzędzi Szybki dostęp.  
  
```  
void RemoveAll();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja usuwa z tego wystąpienia wszystkie polecenia który poprzednich wywołań [CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](#addcommand) dodane.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
