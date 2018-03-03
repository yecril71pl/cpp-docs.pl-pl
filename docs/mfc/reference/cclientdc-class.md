---
title: "Cclientdc — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a92fb471ee30e725cd97bff6cbda8d551c0bc859
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cclientdc-class"></a>Cclientdc — klasa
Odpowiada on za wywoływanie funkcji Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) podczas konstruowania i [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920) w chwili zniszczenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CClientDC : public CDC  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CClientDC::CClientDC](#cclientdc)|Konstruuje `CClientDC` obiekt połączony `CWnd`.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CClientDC::m_hWnd](#m_hwnd)|`HWND` Okna, w których `CClientDC` jest nieprawidłowy.|  
  
## <a name="remarks"></a>Uwagi  
 Oznacza to, że kontekst urządzenia skojarzone z `CClientDC` obiekt jest w klienckim obszarze okna.  
  
 Aby uzyskać więcej informacji na temat `CClientDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cclientdc"></a>CClientDC::CClientDC  
 Konstruuje `CClientDC` obiektu, który uzyskuje dostęp do obszaru klienckiego [CWnd](../../mfc/reference/cwnd-class.md) wskazywana przez `pWnd`.  
  
```  
explicit CClientDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Którego obszaru klienckiego obiektu kontekstu urządzenia będą uzyskiwać dostęp do okna.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor wywołuje funkcję Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871).  
  
 Wystąpił wyjątek (typu `CResourceException`) jest zgłaszany w przypadku systemu Windows `GetDC` wywołać kończy się niepowodzeniem. Kontekst urządzenia nie może być dostępna w przypadku systemu Windows zawiera już przydzielone wszystkie konteksty jego dostępnego urządzenia. Aplikacja konkuruje dla pięciu typowych kontekstach wyświetlania dostępnych w danym momencie w systemie Windows.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>CClientDC::m_hWnd  
 `HWND` z `CWnd` wskaźnik został użyty do utworzenia `CClientDC` obiektu.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_hWnd`jest zmienną chronionych.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CClientDC::CClientDC](#cclientdc).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDI](../../visual-cpp-samples.md)   
 [Klasa CDC](../../mfc/reference/cdc-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDC](../../mfc/reference/cdc-class.md)
