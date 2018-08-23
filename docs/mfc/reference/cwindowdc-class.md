---
title: Klasa CWindowDC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b692d974b5397d73f7e328330f71d8f9688be3e2
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42466151"
---
# <a name="cwindowdc-class"></a>Klasa CWindowDC
Pochodną `CDC`.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CWindowDC : public CDC  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWindowDC::CWindowDC](#cwindowdc)|Konstruuje `CWindowDC` obiektu.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWindowDC::m_hWnd](#m_hwnd)|HWND, do którego należy to `CWindowDC` jest dołączony.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołuje funkcję Windows [GetWindowDC](/windows/desktop/api/winuser/nf-winuser-getwindowdc)podczas konstruowania i [ReleaseDC](/windows/desktop/api/winuser/nf-winuser-releasedc) w trakcie niszczenia. Oznacza to, że `CWindowDC` obiekt uzyskuje dostęp do całego obszaru ekranu [CWnd](../../mfc/reference/cwnd-class.md) (obszary zarówno klient, jak i nieklienckie).  
  
 Aby uzyskać więcej informacji na temat korzystania z `CWindowDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [PRZECHWYTYWANIE ZMIAN DANYCH](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: afxwin.h  
  
##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC  
 Konstruuje `CWindowDC` obiektu, który uzyskuje dostęp do całego obszaru ekranu (zarówno klient, jak i nieklienckie) `CWnd` obiekt wskazywany przez *pWnd*.  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Okno obszaru klienta, którego obiekt kontekstu urządzenia będą miały dostęp.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor wywołuje funkcję Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947).  
  
 Wyjątek (typu `CResourceException`) jest generowany, jeśli Windows `GetWindowDC` wywołanie zakończy się niepowodzeniem. Kontekst urządzenia może nie być dostępne w przypadku Windows został już przydzielony wszystkie jego kontekstów dostępnego urządzenia. Aplikacja konkuruje dla pięciu typowych kontekstach wyświetlania dostępnych w danym momencie w obszarze Windows.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd  
 HWND z `CWnd` wskaźnik jest używany do tworzenia `CWindowDC` obiektu.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_hWnd` jest chronione zmienną typu HWND.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWindowDC::CWindowDC](#cwindowdc).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDC](../../mfc/reference/cdc-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDC](../../mfc/reference/cdc-class.md)
