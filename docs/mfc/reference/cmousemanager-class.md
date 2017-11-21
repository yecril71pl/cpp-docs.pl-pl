---
title: Klasa CMouseManager | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMouseManager
- AFXMOUSEMANAGER/CMouseManager
- AFXMOUSEMANAGER/CMouseManager::AddView
- AFXMOUSEMANAGER/CMouseManager::GetViewDblClickCommand
- AFXMOUSEMANAGER/CMouseManager::GetViewIconId
- AFXMOUSEMANAGER/CMouseManager::GetViewIdByName
- AFXMOUSEMANAGER/CMouseManager::GetViewNames
- AFXMOUSEMANAGER/CMouseManager::LoadState
- AFXMOUSEMANAGER/CMouseManager::SaveState
- AFXMOUSEMANAGER/CMouseManager::SetCommandForDblClk
dev_langs: C++
helpviewer_keywords:
- CMouseManager [MFC], AddView
- CMouseManager [MFC], GetViewDblClickCommand
- CMouseManager [MFC], GetViewIconId
- CMouseManager [MFC], GetViewIdByName
- CMouseManager [MFC], GetViewNames
- CMouseManager [MFC], LoadState
- CMouseManager [MFC], SaveState
- CMouseManager [MFC], SetCommandForDblClk
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e395596ee8decde683c13c12a0c1f2bd33a8cc58
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmousemanager-class"></a>Klasa CMouseManager
Umożliwia użytkownikowi skojarzyć różne polecenia z określonego [CView](../../mfc/reference/cview-class.md) obiektu, gdy użytkownik kliknie dwukrotnie w tym widoku.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMouseManager : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMouseManager::AddView](#addview)|Dodaje `CView` do obiektu **dostosowywania** okno dialogowe. **Dostosowywania** okno dialogowe umożliwia użytkownikowi skojarzyć dwukrotne za pomocą polecenia dla każdej z widoków na liście.|  
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Zwraca polecenie, które jest wykonywane, gdy użytkownik kliknie dwukrotnie wewnątrz podana widoku.|  
|[CMouseManager::GetViewIconId](#getviewiconid)|Zwraca ikony skojarzone z identyfikatorem podana widoku.|  
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Zwraca identyfikator widoku skojarzone z nazwą podana widoku.|  
|[CMouseManager::GetViewNames](#getviewnames)|Pobiera listę wszystkich nazw dodano widoku.|  
|[CMouseManager::LoadState](#loadstate)|Ładunki `CMouseManager` stanu z rejestru systemu Windows.|  
|[CMouseManager::SaveState](#savestate)|Zapisuje `CMouseManager` stanu w rejestrze systemu Windows.|  
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Kojarzy podanego polecenia i podana widoku.|  
  
## <a name="remarks"></a>Uwagi  
 `CMouseManager` Klasy zapewnia zbiór `CView` obiektów. Każdy widok jest identyfikowane przez nazwę i identyfikator. Widoki te są wyświetlane w **dostosowywania** okno dialogowe. Użytkownik może zmienić polecenie, które jest skojarzone z każdym widoku za pośrednictwem **dostosowywania** okno dialogowe. Skojarzone polecenie jest wykonywane, gdy użytkownik kliknie dwukrotnie w tym widoku. Obsługa tego z punktu widzenia kodowania, należy przetworzyć `WM_LBUTTONDBLCLK` komunikat i wywołanie [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) funkcji w kodzie w tym `CView` obiektu...  
  
 Nie należy tworzyć `CMouseManager` obiekt ręcznie. Zostanie on utworzony przez platformę aplikacji. Go zostaną również usunięte automatycznie, gdy użytkownik zamyka aplikację. Aby uzyskać wskaźnika myszy Menedżera aplikacji, należy wywołać [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMouseManager`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmousemanager.h  
  
##  <a name="addview"></a>CMouseManager::AddView  
 Rejestruje [CView](../../mfc/reference/cview-class.md) obiekt z [klasy CMouseManager](../../mfc/reference/cmousemanager-class.md) do obsługi myszy niestandardowe zachowanie.  
  
```  
BOOL AddView(
    int iViewId,  
    UINT uiViewNameResId,  
    UINT uiIconId = 0);

 
BOOL AddView(
    int iId,  
    LPCTSTR lpszViewName,  
    UINT uiIconId = 0);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iViewId`  
 Identyfikator widoku.  
  
 [in]`uiViewNameResId`  
 Identyfikator ciągu zasobu, który odwołuje się do nazwy widoku.  
  
 [in]`uiIconId`  
 Identyfikator widoku ikon.  
  
 [in]`iId`  
 Identyfikator widoku.  
  
 [in]`lpszViewName`  
 Nazwa widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby zapewnić obsługę niestandardowego zachowania, musi być zarejestrowany widoku `CMouseManager` obiektu. Dowolny obiekt pochodną `CView` klasy można zarejestrować przy użyciu Menedżera myszy. Ciąg i ikon skojarzonych z widoku są wyświetlane w **myszy** karcie **Dostosuj** okno dialogowe.  
  
 Jest odpowiedzialny za programisty można tworzyć i obsługiwać Przeglądanie identyfikatorów, takich jak `iViewId` i `iId`.  
  
 Aby uzyskać więcej informacji na temat jak zapewnić zachowanie myszy niestandardowych, zobacz [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak pobrać wskaźnik do `CMouseManager` obiektu za pomocą `CWinAppEx::GetMouseManager` — metoda i `AddView` metoda `CMouseManager` klasy. Następujący fragment kodu jest częścią [próbka zbierania stanu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]  
  
##  <a name="getviewdblclickcommand"></a>CMouseManager::GetViewDblClickCommand  
 Zwraca polecenie, które jest wykonywane, gdy użytkownik kliknie dwukrotnie wewnątrz podana widoku.  
  
```  
UINT GetViewDblClickCommand(int iId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iId`  
 Identyfikator widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator polecenia, czy widok jest skojarzony z polecenia; w przeciwnym razie 0.  
  
##  <a name="getviewiconid"></a>CMouseManager::GetViewIconId  
 Pobiera ikon skojarzonych z identyfikatorem widoku.  
  
```  
UINT GetViewIconId(int iViewId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iViewId`  
 Identyfikator widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator zasobu ikony w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem, jeśli widok nie jest najpierw zarejestrowany za pomocą [CMouseManager::AddView](#addview).  
  
##  <a name="getviewidbyname"></a>CMouseManager::GetViewIdByName  
 Pobiera identyfikator widoku skojarzone z nazwą widoku.  
  
```  
int GetViewIdByName(LPCTSTR lpszName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszName`  
 Nazwa widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator widoku, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda przeszuka zarejestrowanych przy użyciu widoków [CMouseManager::AddView](#addview).  
  
##  <a name="getviewnames"></a>CMouseManager::GetViewNames  
 Pobiera listę nazw wszystkich zarejestrowanych widoku.  
  
```  
void GetViewNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out]`listOfNames`  
 Odwołanie do `CStringList` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wypełnia parametr `listOfNames` z nazwami wszystkich zarejestrowanych przy użyciu widoków [CMouseManager::AddView](#addview).  
  
##  <a name="loadstate"></a>CMouseManager::LoadState  
 Ładuje stan [klasy CMouseManager](../../mfc/reference/cmousemanager-class.md) z rejestru.  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Ścieżka do klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Informacje o stanie załadowany z rejestru zawiera zarejestrowanych widoków, widok identyfikatorów i skojarzone z nimi polecenia. Jeśli parametr `lpszProfileName` jest `NULL`, funkcja ładuje `CMouseManager` danych z domyślnej lokalizacji rejestru kontrolowane przez [CWinAppEx klasy](../../mfc/reference/cwinappex-class.md).  
  
 W większości przypadków nie trzeba bezpośrednio wywoływać tej funkcji. Jest on nazywany jako część procesu inicjalizacji obszaru roboczego. Aby uzyskać więcej informacji na temat procesu inicjowania obszaru roboczego zobacz [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).  
  
##  <a name="savestate"></a>CMouseManager::SaveState  
 Zapisuje stan [klasy CMouseManager](../../mfc/reference/cmousemanager-class.md) w rejestrze.  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`lpszProfileName`  
 Ścieżka do klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Informacje o stanie zapisywane w rejestrze obejmuje wszystkich zarejestrowanych widoków, widok identyfikatorów i skojarzone z nimi polecenia. Jeśli parametr `lpszProfileName` jest `NULL`, ta funkcja zapisuje `CMouseManager` danych do lokalizacji w rejestrze domyślnej kontrolowane przez [CWinAppEx klasy](../../mfc/reference/cwinappex-class.md).  
  
 W większości przypadków nie trzeba bezpośrednio wywoływać tej funkcji. Jest to w ramach procesu roboczego serializacji. Aby uzyskać więcej informacji o procesie roboczym serializacji, zobacz [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
##  <a name="setcommandfordblclk"></a>CMouseManager::SetCommandForDblClk  
 Kojarzy polecenia niestandardowych z widoku, który został wcześniej zarejestrowany przy użyciu Menedżera myszy.  
  
```  
void SetCommandForDblClk(
    int iViewId,  
    UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in]`iViewId`  
 Identyfikator widoku.  
  
 [in]`uiCmd`  
 Identyfikator polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Aby można było skojarzyć polecenia niestandardowych z widoku, najpierw należy zarejestrować widoku przy użyciu [CMouseManager::AddView](#addview). `AddView` Metoda wymaga identyfikatora widoku jako parametr wejściowy. Po zarejestrowaniu widoku można wywołać `CMouseManager::SetCommandForDblClk` z tego samego widoku identyfikator parametr wejściowy dostarczona do `AddView`. Następnie, gdy użytkownik kliknie dwukrotnie myszy w zarejestrowany widoku, aplikacji spowoduje wykonanie polecenia wskazywanym przez `uiCmd.` do obsługi myszy niestandardowe zachowanie, również należy dostosować widok zarejestrowana przy użyciu Menedżera myszy. Aby uzyskać więcej informacji dotyczących zachowania myszy niestandardowych, zobacz [Dostosowywanie klawiatury i myszy]--brokenlink--(.. / customization.md myszy i klawiatury).  
  
 Jeśli `uiCmd` jest ustawiony na wartość 0, określony widok nie jest już skojarzona z poleceniem.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md)



