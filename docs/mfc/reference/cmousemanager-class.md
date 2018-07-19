---
title: Klasa CMouseManager | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d99f0b2ea50e84e3eb5e89d1f2e24a181653893c
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852480"
---
# <a name="cmousemanager-class"></a>Klasa CMouseManager
Umożliwia użytkownikowi skojarzyć różne polecenia z określonym [CView](../../mfc/reference/cview-class.md) obiektu, kiedy użytkownik kliknie dwukrotnie wewnątrz tego widoku.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CMouseManager : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMouseManager::AddView](#addview)|Dodaje `CView` obiekt **dostosowywania** okno dialogowe. **Dostosowywania** okno dialogowe umożliwia użytkownikowi skojarzenie dwukrotne kliknięcie za pomocą polecenia dla każdego z widoków na liście.|  
|[CMouseManager::GetViewDblClickCommand](#getviewdblclickcommand)|Zwraca polecenia, który jest wykonywany, gdy użytkownik kliknie dwukrotnie wewnątrz podana widoku.|  
|[CMouseManager::GetViewIconId](#getviewiconid)|Zwraca ikon skojarzonych z identyfikatorem podana widoku.|  
|[CMouseManager::GetViewIdByName](#getviewidbyname)|Zwraca identyfikator widoku skojarzone z nazwą podany widoku.|  
|[CMouseManager::GetViewNames](#getviewnames)|Pobiera listę wszystkich nazw dodano widok.|  
|[CMouseManager::LoadState](#loadstate)|Ładunki `CMouseManager` stan z rejestru Windows.|  
|[CMouseManager::SaveState](#savestate)|Zapisuje `CMouseManager` stanu do rejestru Windows.|  
|[CMouseManager::SetCommandForDblClk](#setcommandfordblclk)|Kojarzy podanego polecenia i podana widoku.|  
  
## <a name="remarks"></a>Uwagi  
 `CMouseManager` Klasa przechowuje kolekcję `CView` obiektów. Każdy widok jest identyfikowane przez nazwę i identyfikator. Widoki te są wyświetlane w **dostosowywania** okno dialogowe. Użytkownik może zmienić polecenia, które jest skojarzone z każdym widoku przy użyciu **dostosowywania** okno dialogowe. Skojarzone polecenie jest wykonywane, gdy użytkownik kliknie dwukrotnie w tym widoku. Aby to umożliwić, z punktu widzenia kodowania, musi przetwarzać komunikatów WM_LBUTTONDBLCLK i wywołania [CWinAppEx::OnViewDoubleClick](../../mfc/reference/cwinappex-class.md#onviewdoubleclick) funkcji w kodzie, który `CView` obiektu...  
  
 Nie należy tworzyć `CMouseManager` obiektu ręcznie. Zostanie on utworzony przez platformę aplikacji. On również jest niszczony automatycznie przy zamykaniu aplikacji. Aby uzyskać wskaźnik do Menedżera myszy aplikację, należy wywołać [CWinAppEx::GetMouseManager](../../mfc/reference/cwinappex-class.md#getmousemanager).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMouseManager`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmousemanager.h  
  
##  <a name="addview"></a>  CMouseManager::AddView  
 Rejestruje [CView](../../mfc/reference/cview-class.md) obiekt z [klasa CMouseManager](../../mfc/reference/cmousemanager-class.md) do obsługi myszy niestandardowe zachowania.  
  
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
 [in] *iViewId*  
 Identyfikator widoku.  
  
 [in] *uiViewNameResId*  
 Identyfikator ciągu zasobu, który odwołuje się do nazwy widoku.  
  
 [in] *uiIconId*  
 Identyfikator widoku ikon.  
  
 [in] *iId*  
 Identyfikator widoku.  
  
 [in] *lpszViewName*  
 Nazwa widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aby można było obsługiwać mysz niestandardowe zachowanie, widok muszą być zarejestrowane w usłudze `CMouseManager` obiektu. Każdy obiekt jest pochodną `CView` klasy można zarejestrować za pomocą Menedżera myszy. Parametry i ikon skojarzonych z widoku są wyświetlane w **myszy** karcie **Dostosuj** okno dialogowe.  
  
 Jest odpowiedzialny za programisty do tworzenia i obsługi Przeglądanie identyfikatorów, takich jak *iViewId* i *iId*.  
  
 Aby uzyskać więcej informacji na temat jak zapewnić zachowanie myszy niestandardowych, zobacz [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md).  
  
### <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak pobrać wskaźnika do `CMouseManager` obiektu za pomocą `CWinAppEx::GetMouseManager` metody i `AddView` method in Class metoda `CMouseManager` klasy. Ten fragment kodu jest częścią [próbka zbierania stanu](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection#4](../../mfc/reference/codesnippet/cpp/cmousemanager-class_1.cpp)]  
  
##  <a name="getviewdblclickcommand"></a>  CMouseManager::GetViewDblClickCommand  
 Zwraca polecenia, który jest wykonywany, gdy użytkownik kliknie dwukrotnie wewnątrz podana widoku.  
  
```  
UINT GetViewDblClickCommand(int iId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iId*  
 Identyfikator widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator polecenia, jeśli widok jest skojarzone z poleceniem; w przeciwnym razie 0.  
  
##  <a name="getviewiconid"></a>  CMouseManager::GetViewIconId  
 Pobiera ikonę skojarzony identyfikator widoku.  
  
```  
UINT GetViewIconId(int iViewId) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iViewId*  
 Identyfikator widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator zasobu ikony w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zakończy się niepowodzeniem, jeśli widok jest najpierw niezarejestrowany przy użyciu [CMouseManager::AddView](#addview).  
  
##  <a name="getviewidbyname"></a>  CMouseManager::GetViewIdByName  
 Pobiera identyfikator widoku skojarzone z nazwą widoku.  
  
```  
int GetViewIdByName(LPCTSTR lpszName) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszName*  
 Nazwa widoku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Identyfikator widoku, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Metoda ta wyszukuje za pośrednictwem widoków zarejestrowane przy użyciu [CMouseManager::AddView](#addview).  
  
##  <a name="getviewnames"></a>  CMouseManager::GetViewNames  
 Pobiera listę nazw wszystkich zarejestrowanych widoku.  
  
```  
void GetViewNames(CStringList& listOfNames) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [out] *listOfNames*  
 Odwołanie do `CStringList` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wypełni parametr `listOfNames` z nazwami wszystkich widoków, które są zarejestrowane przy użyciu [CMouseManager::AddView](#addview).  
  
##  <a name="loadstate"></a>  CMouseManager::LoadState  
 Ładuje stan [klasa CMouseManager](../../mfc/reference/cmousemanager-class.md) z rejestru.  
  
```  
BOOL LoadState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszProfileName*  
 Ścieżki klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Informacje o stanie załadować z rejestru zawiera zarejestrowane widoki, Wyświetl identyfikatory i skojarzone z nimi polecenia. Jeśli parametr *lpszProfileName* ma wartość NULL, funkcja ładuje `CMouseManager` dane z lokalizacji rejestru domyślne, które są kontrolowane przez [klasa CWinAppEx](../../mfc/reference/cwinappex-class.md).  
  
 W większości przypadków nie trzeba bezpośrednio wywołać tę funkcję. Jest on nazywany jako część procesu inicjowania obszaru roboczego. Aby uzyskać więcej informacji na temat procesu inicjowania obszaru roboczego, zobacz [CWinAppEx::LoadState](../../mfc/reference/cwinappex-class.md#loadstate).  
  
##  <a name="savestate"></a>  CMouseManager::SaveState  
 Zapisuje stan [klasa CMouseManager](../../mfc/reference/cmousemanager-class.md) w rejestrze.  
  
```  
BOOL SaveState(LPCTSTR lpszProfileName = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *lpszProfileName*  
 Ścieżki klucza rejestru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Informacje o stanie zapisywane w rejestrze zawiera wszystkie zarejestrowane widoki, Wyświetl identyfikatory i skojarzone z nimi polecenia. Jeśli parametr *lpszProfileName* ma wartość NULL, funkcja ta zapisuje `CMouseManager` danych w domyślnej lokalizacji rejestru, który jest kontrolowany przez [klasa CWinAppEx](../../mfc/reference/cwinappex-class.md).  
  
 W większości przypadków nie trzeba bezpośrednio wywołać tę funkcję. Jest on nazywany jako część procesu serializacji obszaru roboczego. Aby uzyskać więcej informacji na temat procesu serializacji obszaru roboczego, zobacz [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
##  <a name="setcommandfordblclk"></a>  CMouseManager::SetCommandForDblClk  
 Kojarzy polecenia niestandardowego przy użyciu widoku, który został wcześniej zarejestrowany za pomocą Menedżera myszy.  
  
```  
void SetCommandForDblClk(
    int iViewId,  
    UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *iViewId*  
 Identyfikator widoku.  
  
 [in] *uiCmd*  
 Identyfikator polecenia.  
  
### <a name="remarks"></a>Uwagi  
 Aby można było skojarzyć polecenie niestandardowe przy użyciu widoku, najpierw musisz się zarejestrować widoku przy użyciu [CMouseManager::AddView](#addview). `AddView` Wymaga, aby identyfikator widoku, jako parametr wejściowy. Po zarejestrowaniu się widok, wywołując `CMouseManager::SetCommandForDblClk` przy użyciu tego samego widoku danych wejściowych parametr identyfikatora dostarczona do `AddView`. Później, gdy użytkownik kliknie dwukrotnie myszy w widoku zarejestrowanych, aplikacji spowoduje wykonanie polecenia wskazywanym przez *uiCmd.* Aby zapewnić obsługę zachowanie myszy niestandardowe, należy również dostosować widok zarejestrowane przy użyciu Menedżera myszy. Aby uzyskać więcej informacji o zachowanie myszy niestandardowych, zobacz [Dostosowywanie klawiatury i myszy](../keyboard-and-mouse-customization.md).  
  
 Jeśli *uiCmd* jest ustawiona na wartość 0, określony widok nie jest już skojarzona z poleceniem.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasy](../../mfc/reference/mfc-classes.md)   
 [Klasa CWinAppEx](../../mfc/reference/cwinappex-class.md)   
 [Dostosowywanie klawiatury i myszy](../../mfc/keyboard-and-mouse-customization.md)



