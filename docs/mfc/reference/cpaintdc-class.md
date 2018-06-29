---
title: Cpaintdc — klasa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 496c06fe7550598eeeb4136b233f39079d7425e9
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078222"
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
|[CPaintDC::m_ps](#m_ps)|Zawiera [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md) używany do rysowania obszaru klienckiego.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPaintDC::m_hWnd](#m_hwnd)|`HWND` Do której należy `CPaintDC` obiekt jest dołączony.|  
  
## <a name="remarks"></a>Uwagi  
 Wykonuje [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) podczas konstruowania i [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) w chwili zniszczenia.  
  
 A `CPaintDC` obiektu można używać tylko w przypadku odpowiedzi na [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) komunikatu, zazwyczaj w Twojej `OnPaint` funkcji członkowskiej obsługi wiadomości.  
  
 Aby uzyskać więcej informacji na temat używania `CPaintDC`, zobacz [konteksty urządzenia](../../mfc/device-contexts.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CPaintDC`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC  
 Konstruuje `CPaintDC` obiektu przygotowuje okna aplikacji do rysowania i przechowuje [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md) struktury w [m_ps](#m_ps) zmiennej członkowskiej.  
  
```  
explicit CPaintDC(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Wskazuje `CWnd` obiektu, do którego `CPaintDC` należy obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wystąpił wyjątek (typu `CResourceException`) jest zgłaszany w przypadku systemu Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) wywołać kończy się niepowodzeniem. Kontekst urządzenia nie może być dostępna w przypadku systemu Windows zawiera już przydzielone wszystkie konteksty jego dostępnego urządzenia. Aplikacja konkuruje dla pięciu typowych kontekstach wyświetlania dostępnych w danym momencie w systemie Windows.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]  
  
##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd  
 `HWND` Do której należy `CPaintDC` obiekt jest dołączony.  
  
```  
HWND m_hWnd;  
```  
  
### <a name="remarks"></a>Uwagi  
 *m_hWnd* jest chronionej zmiennej typu `HWND`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]  
  
##  <a name="m_ps"></a>  CPaintDC::m_ps  
 `m_ps` jest to zmienna publicznego elementu członkowskiego typu [PAINTSTRUCT](../../mfc/reference/paintstruct-structure.md).  
  
```  
PAINTSTRUCT m_ps;  
```  
  
### <a name="remarks"></a>Uwagi  
 Jest `PAINTSTRUCT` jest przekazywany do i wypełnia [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).  
  
 `PAINTSTRUCT` Zawiera informacje, które aplikacja używa do malowania obszar kliencki okno skojarzone z `CPaintDC` obiektu.  
  
 Należy pamiętać, że masz dostęp uchwyt kontekstu urządzenia za pośrednictwem `PAINTSTRUCT`. Można jednak dostępu dojście więcej bezpośrednio za pomocą `m_hDC` zmiennej członkowskiej który `CPaintDC` dziedziczy `CDC`.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CPaintDC::m_hWnd](#m_hwnd).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC MDI](../../visual-cpp-samples.md)   
 [Klasa CDC](../../mfc/reference/cdc-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



