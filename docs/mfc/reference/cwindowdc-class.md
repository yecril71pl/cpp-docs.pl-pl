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
ms.openlocfilehash: 8b757da27f2b4ae79a0192df0598f833b3d1e7b9
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121545"
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
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWindowDC::m_hWnd](#m_hwnd)|Właściwość HWND, do której należy `CWindowDC` jest dołączony.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołuje funkcję Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)podczas konstruowania i [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx) w chwili zniszczenia. Oznacza to, że `CWindowDC` obiekt uzyskuje dostęp do obszaru cały ekran [CWnd](../../mfc/reference/cwnd-class.md) (obszary zarówno klient, jak i nieklienckim).  
  
 Aby uzyskać więcej informacji na temat używania `CWindowDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: afxwin.h  
  
##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC  
 Konstruuje `CWindowDC` obiektu, który uzyskuje dostęp do całego obszaru ekranu (klient i nieklienckim) `CWnd` obiekt wskazywany przez *pWnd*.  
  
```  
explicit CWindowDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Którego obszaru klienckiego obiektu kontekstu urządzenia będą uzyskiwać dostęp do okna.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor wywołuje funkcję Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947).  
  
 Wystąpił wyjątek (typu `CResourceException`) jest zgłaszany w przypadku systemu Windows `GetWindowDC` wywołać kończy się niepowodzeniem. Kontekst urządzenia nie może być dostępna w przypadku systemu Windows zawiera już przydzielone wszystkie konteksty jego dostępnego urządzenia. Aplikacja konkuruje dla pięciu typowych kontekstach wyświetlania dostępnych w danym momencie w systemie Windows.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd  
 Właściwość HWND z `CWnd` wskaźnika jest używany do tworzenia `CWindowDC` obiektu.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_hWnd` jest chronionej zmiennej typu HWND.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CWindowDC::CWindowDC](#cwindowdc).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDC](../../mfc/reference/cdc-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDC](../../mfc/reference/cdc-class.md)
