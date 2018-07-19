---
title: Klasa CPaintDC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
dev_langs:
- C++
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 119a4e1b39d86ef2d12565fd593ce2124cef5bd5
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848918"
---
# <a name="cpaintdc-class"></a>Cpaintdc — klasa
Kontekst urządzenia klasą pochodną [CDC](../../mfc/reference/cdc-class.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPaintDC : public CDC  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPaintDC::CPaintDC](#cpaintdc)|Konstruuje `CPaintDC` podłączone do określonego [CWnd](../../mfc/reference/cwnd-class.md).|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPaintDC::m_ps](#m_ps)|Zawiera [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md) używany do rysowania obszaru klienta.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPaintDC::m_hWnd](#m_hwnd)|HWND, do którego należy to `CPaintDC` obiekt jest dołączony.|  
  
## <a name="remarks"></a>Uwagi  
 Wykonuje [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) podczas konstruowania i [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) w trakcie niszczenia.  
  
 A `CPaintDC` obiekt może być używany tylko w przypadku reagowania na [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) komunikatu, zazwyczaj w swojej `OnPaint` funkcja elementu członkowskiego program obsługi komunikatów.  
  
 Aby uzyskać więcej informacji na temat korzystania z `CPaintDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [PRZECHWYTYWANIE ZMIAN DANYCH](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC  
 Konstruuje `CPaintDC` przygotowuje okna aplikacji rysowania obiektu i przechowuje [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md) struktury w [m_ps](#m_ps) zmiennej składowej.  
  
```  
explicit CPaintDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wskazuje `CWnd` obiekt, do którego `CPaintDC` należy obiekt.  
  
### <a name="remarks"></a>Uwagi  
 Wyjątek (typu `CResourceException`) jest generowany, jeśli Windows [getdc —](http://msdn.microsoft.com/library/windows/desktop/dd144871) wywołanie zakończy się niepowodzeniem. Kontekst urządzenia może nie być dostępne w przypadku Windows został już przydzielony wszystkie jego kontekstów dostępnego urządzenia. Aplikacja konkuruje dla pięciu typowych kontekstach wyświetlania dostępnych w danym momencie w obszarze Windows.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd  
 `HWND` Do którego należy to `CPaintDC` obiekt jest dołączony.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Uwagi  
 *m_hWnd* jest chroniony zmienną typu HWND.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]  
  
##  <a name="m_ps"></a>  CPaintDC::m_ps  
 `m_ps` jest to zmienna członka publicznego typu [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md).  
  
```  
PAINTSTRUCT m_ps;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jest `PAINTSTRUCT` który jest przekazywany do i wypełnione przez [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).  
  
 `PAINTSTRUCT` Zawiera informacje, którego używa aplikacja do malowania obszaru klienckiego okna skojarzony `CPaintDC` obiektu.  
  
 Należy pamiętać, dostęp uchwyt kontekstu urządzenia za pośrednictwem `PAINTSTRUCT`. Można jednak uzyskać dostępu uchwyt bardziej bezpośrednio za pośrednictwem `m_hDC` zmiennej składowej, `CPaintDC` dziedziczy przechwytywania zmian danych.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPaintDC::m_hWnd](#m_hwnd).  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC MDI](../../visual-cpp-samples.md)   
 [Klasa CDC](../../mfc/reference/cdc-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



