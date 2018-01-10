---
title: Klasa CWinFormsDialog | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
dev_langs: C++
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c59faec7fc981cff31bea4ce6e846d89d0b8bf99
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cwinformsdialog-class"></a>Klasa CWinFormsDialog
Otoka dla klasy okien dialogowych MFC, obsługującym kontrolki użytkownika formularza systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
    public CDialog  
```  
  
#### <a name="parameters"></a>Parametry  
 `TManagedControl`  
 Kontrolki użytkownika platformy .NET Framework ma być wyświetlany w aplikacji MFC.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Konstruuje `CWinFormsDialog` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWinFormsDialog::GetControl](#getcontrol)|Pobiera odwołanie do formantu użytkownika formularzy systemu Windows.|  
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Pobiera uchwyt okna do kontrolki użytkownika formularzy systemu Windows.|  
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Inicjowanie okna dialogowego MFC przez utworzenie i hostowanie formantu użytkownika formularzy systemu Windows na nim.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa||  
|----------|-|  
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|Zastępuje [CWinFormsDialog::GetControl](#getcontrol) w wyrażeniach.|  
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|Rzutuje typu jako odwołanie do formantu użytkownika formularzy systemu Windows.|  
  
## <a name="remarks"></a>Uwagi  
 `CWinFormsDialog`Otoka dla klasy okien dialogowych MFC jest ( [cdialog —](../../mfc/reference/cdialog-class.md)) obsługującego kontrolki użytkownika formularza systemu Windows. Dzięki temu wyświetlania formantów .NET Framework na modalne i niemodalne okno dialogowe MFC.  
  
 Aby uzyskać więcej informacji na temat używania formularzy systemu Windows, zobacz [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) i [hostowanie formantu użytkownika formularza systemu Windows jako okna dialogowego MFC](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwinforms.h  
  
##  <a name="cwinformsdialog"></a>CWinFormsDialog::CWinFormsDialog  
 Konstruuje `CWinFormsDialog` obiektu.  
  
```  
CWinFormsDialog(UINT nIDTemplate = IDD);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDTemplate`  
 Zawiera identyfikator zasobu szablon — okno dialogowe. Edytor okien dialogowych umożliwia tworzenie szablonu okna dialogowego i zapisz go w pliku skryptu zasobu aplikacji. Aby uzyskać więcej informacji na szablony okna dialogowego, zobacz [cdialog — klasa](../../mfc/reference/cdialog-class.md).  
  
##  <a name="getcontrol"></a>CWinFormsDialog::GetControl  
 Pobiera odwołanie do formantu użytkownika formularzy systemu Windows.  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca odwołanie do formantu formularzy systemu Windows w oknie dialogowym MFC.  
  
##  <a name="getcontrolhandle"></a>CWinFormsDialog::GetControlHandle  
 Pobiera uchwyt okna do kontrolki użytkownika formularzy systemu Windows.  
  
```  
inline HWND GetControlHandle() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca uchwyt okna do formantu użytkownika formularzy systemu Windows.  
  
##  <a name="oninitdialog"></a>CWinFormsDialog::OnInitDialog  
 Inicjowanie okna dialogowego MFC przez utworzenie i hostowanie formantu użytkownika formularzy systemu Windows na nim.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość logiczna, która określa, czy aplikacja ma fokus wprowadzania formantów w oknie dialogowym. Jeśli `OnInitDialog` zwraca różną od zera, Windows ustawia fokus wprowadzania do pierwszego formantu w oknie dialogowym. Ta metoda może zwracać 0 tylko wtedy, gdy aplikacja ma jawnie ustawiona fokus wprowadzania do formantów w oknie dialogowym.  
  
### <a name="remarks"></a>Uwagi  
 Podczas tworzenia okna dialogowego MFC (przy użyciu [Utwórz](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect), lub [DoModal](../../mfc/reference/cdialog-class.md#domodal) metody dziedziczone z [cdialog —](../../mfc/reference/cdialog-class.md)), `WM_INITDIALOG` jest wysyłany komunikat, a ta metoda jest wywoływana. Tworzy wystąpienie formantu formularzy systemu Windows w oknie dialogowym i dopasowuje rozmiar okna dialogowego, aby pomieścić rozmiaru kontrolki użytkownika. Następnie obsługuje nowego formantu w oknie dialogowym MFC.  
  
 Przesłonić tę funkcję elementu członkowskiego, jeśli należy przeprowadzić specjalnego przetwarzania, gdy okno dialogowe jest inicjowany. Aby uzyskać więcej informacji na temat używania tej metody, zobacz [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).  
  
##  <a name="operator_-_gt"></a>CWinFormsDialog::operator-&gt;  
 Zastępuje [CWinFormsDialog::GetControl](#getcontrol) w wyrażeniach.  
  
```  
inline TManagedControl^  operator->() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator oferuje wygodny składnię, która zastępuje `GetControl` w wyrażeniach.  
  
 Aby uzyskać informacje na temat używania formularzy systemu Windows, temacie [za pomocą formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_tmanagedcontrol_xor"></a>CWinFormsDialog::operator TManagedControl ^  
 Rzutuje typu jako odwołanie do formantu użytkownika formularzy systemu Windows.  
  
```  
inline operator TManagedControl^() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator rzutuje typu jako odwołanie do formantu formularzy systemu Windows. Służy do przekazywania `CWinFormsDialog<TManagedControl>` okno dialogowe do funkcji, które akceptują wskaźnik do obiektu formantu użytkownika formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)   
 [Klasa CDialog](../../mfc/reference/cdialog-class.md)
