---
title: Klasa CComControl | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComControl
- ATLCTL/ATL::CComControl
- ATLCTL/ATL::CComControl::CComControl
- ATLCTL/ATL::CComControl::ControlQueryInterface
- ATLCTL/ATL::CComControl::CreateControlWindow
- ATLCTL/ATL::CComControl::FireOnChanged
- ATLCTL/ATL::CComControl::FireOnRequestEdit
- ATLCTL/ATL::CComControl::MessageBox
dev_langs:
- C++
helpviewer_keywords:
- control flags
- CComControlBase class, CComControl class
- stock properties, ATL
- CComControl class
- controls [ATL], control helper functions
- ambient properties
- controls [ATL], properties
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae81e2b6beac11f94f8d117b004da2f8d0db8724
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcontrol-class"></a>Klasa CComControl
Ta klasa dostarcza metody do tworzenia i zarządzania kontrolek ALT.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T, class WinBase = CWindowImpl<T>>  
class ATL_NO_VTABLE CComControl : public CComControlBase,
    public WinBase;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasa implementująca formantu.  
  
 *WinBase*  
 Klasa podstawowa, która implementuje funkcje okien. Domyślnie [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComControl::CComControl](#ccomcontrol)|Konstruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComControl::ControlQueryInterface](#controlqueryinterface)|Pobiera wskaźnik do żądanego interfejsu.|  
|[CComControl::CreateControlWindow](#createcontrolwindow)|Utworzenie okna dla kontrolki.|  
|[CComControl::FireOnChanged](#fireonchanged)|Powiadamia zbiornika kontenera, który zmieniono właściwość formantu.|  
|[CComControl::FireOnRequestEdit](#fireonrequestedit)|Powiadamia kontenera obiektu sink właściwości formantu o zbliżającym się zmienić i że obiektu prosi obiekt sink postępowania.|  
|[CComControl::MessageBox](#messagebox)|Wywołanie tej metody do tworzenia, wyświetlania i działać okno komunikatu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComControl`to zestaw funkcji pomocnika przydatne kontroli i elementy członkowskie danych istotnych dla kontrolek ALT. Podczas tworzenia formantu standardowego lub formantu DHTML przy użyciu Kreator formantu ATL, Kreator automatycznie uzyskuje klasy z `CComControl`. `CComControl`większość jego metody pochodzi [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).  
  
 Aby uzyskać więcej informacji o tworzeniu formantu, zobacz [ALT — samouczek](../../atl/active-template-library-atl-tutorial.md). Aby uzyskać więcej informacji o Kreatorze Projekt ATL, zobacz artykuł [tworzenie Projekt ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Dla pokaz `CComControl` metod i elementów członkowskich danych, zobacz [OK](../../visual-cpp-samples.md) próbki.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlctl.h  
  
##  <a name="ccomcontrol"></a>CComControl::CComControl  
 Konstruktor.  
  
```
CComControl();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CComControlBase](ccomcontrolbase-class.md#ccomcontrolbase) konstruktora, przekazywanie `m_hWnd` dziedziczony element członkowski danych za pośrednictwem [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
##  <a name="controlqueryinterface"></a>CComControl::ControlQueryInterface  
 Pobiera wskaźnik do żądanego interfejsu.  
  
```
virtual HRESULT ControlQueryInterface(const IID& iid, void** ppv);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [in] Identyfikator GUID żądanego interfejsu.  
  
 `ppv`  
 [out] Wskaźnik do wskaźnika interfejsu identyfikowane przez `iid`, lub **NULL** Jeśli nie można odnaleźć interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Obsługuje tylko interfejsy COM tabeli mapy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrol-class_1.cpp)]  
  
##  <a name="createcontrolwindow"></a>CComControl::CreateControlWindow  
 Domyślnie tworzy okna dla kontrolki przez wywołanie metody `CWindowImpl::Create`.  
  
```
virtual HWND CreateControlWindow(HWND hWndParent, RECT& rcPos);
```  
  
### <a name="parameters"></a>Parametry  
 `hWndParent`  
 [in] Dojście do okna nadrzędnego lub właściciela. Należy podać prawidłowy uchwyt okna. Okno kontrolki jest ograniczona do obszaru okna nadrzędnego.  
  
 `rcPos`  
 [in] Początkowy rozmiar i położenie okna, które ma zostać utworzony.  
  
### <a name="remarks"></a>Uwagi  
 Przesłonić tę metodę, jeśli chcesz zrobić coś innego niż tworzenie jednego okna, na przykład, aby utworzyć dwa okna, z których jedna staje się narzędzi dla formantu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#16](../../atl/codesnippet/cpp/ccomcontrol-class_2.cpp)]  
  
##  <a name="fireonchanged"></a>CComControl::FireOnChanged  
 Powiadamia zbiornika kontenera, który zmieniono właściwość formantu.  
  
```
HRESULT FireOnChanged(DISPID dispID);
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator dispID*  
 [in] Identyfikator właściwości, która została zmieniona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pochodną klasy formantu [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), ta metoda wywołuje [CFirePropNotifyEvent::FireOnChanged](cfirepropnotifyevent-class.md#fireonchanged) powiadomiono wszystkie połączone `IPropertyNotifySink` interfejsów określonego formantu Właściwość zostanie zmieniona. Jeśli nie jest pochodną klasy formantu `IPropertyNotifySink`, ta metoda zwraca `S_OK`. 
  
 Ta metoda jest bezpiecznie wywołać nawet wtedy, gdy formant nie obsługuje punkty połączenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#17](../../atl/codesnippet/cpp/ccomcontrol-class_3.cpp)]  
  
##  <a name="fireonrequestedit"></a>CComControl::FireOnRequestEdit  
 Powiadamia kontenera obiektu sink właściwości formantu o zbliżającym się zmienić i że obiektu prosi obiekt sink postępowania.  
  
```
HRESULT FireOnRequestEdit(DISPID dispID);
```  
  
### <a name="parameters"></a>Parametry  
 *Identyfikator dispID*  
 [in] Identyfikator właściwości zostać zmieniona.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pochodną klasy formantu [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638), ta metoda wywołuje [CFirePropNotifyEvent::FireOnRequestEdit](cfirepropnotifyevent-class.md#fireonrequestedit) powiadomiono wszystkie połączone `IPropertyNotifySink` interfejsów określony Właściwość formantu ma zostać zmieniona. Jeśli nie jest pochodną klasy formantu `IPropertyNotifySink`, ta metoda zwraca `S_OK`.  

  
 Ta metoda jest bezpiecznie wywołać nawet wtedy, gdy formant nie obsługuje punkty połączenia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#18](../../atl/codesnippet/cpp/ccomcontrol-class_4.cpp)]  
  
##  <a name="messagebox"></a>CComControl::MessageBox  
 Wywołanie tej metody do tworzenia, wyświetlania i działać okno komunikatu.  
  
```
int MessageBox(
    LPCTSTR lpszText,
    LPCTSTR lpszCaption = _T(""),
    UINT nType = MB_OK);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszText`  
 Tekst, który ma być wyświetlany w oknie komunikatu.  
  
 `lpszCaption`  
 Tytuł okna dialogowego. Jeśli wartość NULL (ustawienie domyślne), tytuł "Error" jest używany.  
  
 `nType`  
 Określa zawartość i zachowanie okna dialogowego. Zobacz [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) wpis w dokumentacji zestawu SDK systemu Windows zawiera listę dostępnych pól inny komunikat. Domyślnie udostępnia prostą **OK** przycisku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość całkowitą, określając jedną z wartości elementu menu kategorii [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) w dokumentacji zestawu SDK systemu Windows.  
  
### <a name="remarks"></a>Uwagi  
 `MessageBox`jest przydatne podczas rozwoju i w prosty sposób, aby wyświetlić błąd lub ostrzeżenie dla użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWindowImpl](../../atl/reference/cwindowimpl-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa CComControlBase](../../atl/reference/ccomcontrolbase-class.md)   
 [Klasa CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)
