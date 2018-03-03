---
title: "Cdataexchange — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
dev_langs:
- C++
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1e56df3ec4604a02ba9cf1075152a11eefe7e28f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdataexchange-class"></a>Cdataexchange — klasa
Obsługuje wymiana danych okna dialogowego (DDX) i używane przez Microsoft Foundation classes procedury weryfikacji (DDV) danych okna dialogowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDataExchange  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDataExchange::CDataExchange](#cdataexchange)|Konstruuje `CDataExchange` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDataExchange::Fail](#fail)|Wywoływany w przypadku niepowodzenia weryfikacji. Resetuje fokus do poprzedniego formantu i zgłasza wyjątek.|  
|[CDataExchange::PrepareCtrl](#preparectrl)|Określony formant przygotowuje do weryfikacji lub wymiany danych. Na użytek nonedit kontrolki.|  
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Przygotowuje kontrolki edycji określony na potrzeby weryfikacji lub wymiany danych.|  
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Określony formant OLE przygotowuje do weryfikacji lub wymiany danych. Na użytek nonedit kontrolki.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Flaga dla kierunku DDX i DDV.|  
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|Okna dialogowego lub okna, gdy dane programu exchange ma miejsce.|  
  
## <a name="remarks"></a>Uwagi  
 `CDataExchange`nie ma klasy podstawowej.  
  
 Klasa używana podczas pisania procedury wymiany danych w niestandardowe typy danych lub formantów, lub jeśli piszesz własne procedury walidacji danych. Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [26 Uwaga techniczna](../../mfc/tn026-ddx-and-ddv-routines.md). Omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md) i [okien dialogowych](../../mfc/dialog-boxes.md).  
  
 A `CDataExchange` obiektu zawiera informacje o kontekście potrzebnego do podjęcia DDX i DDV Umieść. Flaga `m_bSaveAndValidate` jest **FALSE** po DDX jest używany do wypełniania wartości początkowe formantów okna dialogowego z elementów członkowskich danych. Flaga `m_bSaveAndValidate` jest **TRUE** po DDX jest używana do ustawiania bieżące wartości formantów okna dialogowego do elementów członkowskich danych i gdy DDV jest używany do sprawdzania poprawności wartości danych. W przypadku niepowodzenia weryfikacji DDV procedury DDV wyświetli okno komunikatu wyjaśniający błąd danych wejściowych. Następnie wywoła procedurę DDV **niepowodzenie** zresetować fokus do formantu ataku i Zgłoś wyjątek, aby zatrzymać proces sprawdzania poprawności.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CDataExchange`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="cdataexchange"></a>CDataExchange::CDataExchange  
 Wywołanie tej funkcji Członkowskich do skonstruowania `CDataExchange` obiektu.  
  
```  
CDataExchange(
    CWnd* pDlgWnd,  
    BOOL bSaveAndValidate);
```  
  
### <a name="parameters"></a>Parametry  
 *pDlgWnd*  
 Wskaźnik do okna nadrzędnego, który zawiera formant. Zazwyczaj jest to [cdialog —](../../mfc/reference/cdialog-class.md)-pochodzi z obiektu.  
  
 `bSaveAndValidate`  
 Jeśli **TRUE**, ten obiekt sprawdza poprawność danych, a następnie zapisuje dane z kontrolki do elementów członkowskich. Jeśli **FALSE**, ten obiekt będzie przenieść dane z elementów członkowskich do kontrolek.  
  
### <a name="remarks"></a>Uwagi  
 Utworzyć `CDataExchange` obiektu samodzielnie do przechowywania dodatkowych informacji w obiekcie wymiany danych do przekazania do Twojej okna [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) funkcji członkowskiej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]  
  
##  <a name="fail"></a>CDataExchange::Fail  
 Struktura wywołuje funkcji członkowskiej, gdy operacja sprawdzania poprawności (DDV) danych okna dialogowego nie powiodło się.  
  
```  
void Fail();
```  
  
### <a name="remarks"></a>Uwagi  
 **Niepowodzenie** przywraca fokus i wybieranie kontroli, których Weryfikacja nie powiodła się (jeśli jest, aby przywrócić). **Niepowodzenie** następnie zgłasza wyjątek typu [CUserException](../../mfc/reference/cuserexception-class.md) Aby zatrzymać proces sprawdzania poprawności. Wyjątek powoduje, że okno komunikatu wyjaśniający błąd, który będzie wyświetlany. Po DDV sprawdzania poprawności zakończy się niepowodzeniem, użytkownik może ponownie danych w formancie ataku.  
  
 Można wywołać implementors niestandardowe procedury DDV **niepowodzenie** z ich procedury w przypadku niepowodzenia weryfikacji.  
  
 Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [26 Uwaga techniczna](../../mfc/tn026-ddx-and-ddv-routines.md). Omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md) i [tematy — okno dialogowe](../../mfc/dialog-boxes.md).  
  
##  <a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate  
 Ta flaga wskazuje kierunek operacji wymiana (DDX) danych okna dialogowego.  
  
```  
BOOL m_bSaveAndValidate;  
```  
  
### <a name="remarks"></a>Uwagi  
 Flaga jest różna od zera, jeśli `CDataExchange` obiekt jest używany do przenoszenia danych z formantów okna dialogowego do elementów członkowskich danych klasy okien dialogowych po użytkownik edytuje kontrolki. Flaga wynosi zero, jeśli obiekt jest używany do inicjowania formantów okna dialogowego z elementów członkowskich danych klasy okien dialogowych.  
  
 Flagi również jest niezerowa podczas Walidacja danych okna dialogowego (DDV).  
  
 Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [26 Uwaga techniczna](../../mfc/tn026-ddx-and-ddv-routines.md). Omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md) i [tematy — okno dialogowe](../../mfc/dialog-boxes.md).  
  
##  <a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd  
 Zawiera wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, dla których okna dialogowego wymiany danych (DDX) lub sprawdzania poprawności (DDV) ma miejsce.  
  
```  
CWnd* m_pDlgWnd;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten obiekt jest zwykle [cdialog —](../../mfc/reference/cdialog-class.md) obiektu. Implementors niestandardowe procedury DDX i DDV umożliwia uzyskiwanie dostępu do okna dialogowego, które zawiera formanty działają na ten wskaźnik.  
  
 Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [26 Uwaga techniczna](../../mfc/tn026-ddx-and-ddv-routines.md). Omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md) i [tematy — okno dialogowe](../../mfc/dialog-boxes.md).  
  
##  <a name="preparectrl"></a>CDataExchange::PrepareCtrl  
 Struktura wywołuje tę funkcję elementu członkowskiego, aby przygotować określony formant wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV).  
  
```  
HWND PrepareCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDC`  
 Identyfikator formantu, aby móc przywrócić DDX i DDV.  
  
### <a name="return-value"></a>Wartość zwracana  
 `HWND` Przygotowywany DDX i DDV formantu.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [PrepareEditCtrl](#prepareeditctrl) dla formantów edycyjnych; Użyj tej funkcji Członkowskich dla innych formantów.  
  
 Przygotowanie składa się z przechowywania formantu `HWND` w `CDataExchange` klasy. Platformę używa tego dojścia do przywrócenia fokus do wcześniej ukierunkowanych kontroli w przypadku awarii DDX i DDV.  
  
 Implementors niestandardowe procedury DDX i DDV powinny wywoływać `PrepareCtrl` dla wszystkich kontrolek bez edycji, dla których są wymiany danych za pomocą DDX lub Sprawdzanie poprawności danych za pośrednictwem DDV.  
  
 Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [26 Uwaga techniczna](../../mfc/tn026-ddx-and-ddv-routines.md). Omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md) i [tematy — okno dialogowe](../../mfc/dialog-boxes.md).  
  
##  <a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl  
 Struktura wywołuje tę funkcję elementu członkowskiego, aby przygotować kontrolki edycji określony wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV).  
  
```  
HWND PrepareEditCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDC`  
 Identyfikator formantu edycji można przygotować DDX i DDV.  
  
### <a name="return-value"></a>Wartość zwracana  
 `HWND` Przygotowywany DDX i DDV kontrolki edycji.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [PrepareCtrl](#preparectrl) zamiast tego dla wszystkich kontrolek bez edycji.  
  
 Przygotowanie składa się z dwóch czynności. Najpierw `PrepareEditCtrl` przechowuje formantu `HWND` w `CDataExchange` klasy. Platformę używa tego dojścia do przywrócenia fokus do wcześniej ukierunkowanych kontroli w przypadku awarii DDX i DDV. Drugi, `PrepareEditCtrl` ustawia flagę `CDataExchange` klasy, aby wskazać, że formant, którego dane są wymieniane lub zweryfikowana to formant edycji.  
  
 Implementors niestandardowe procedury DDX i DDV powinny wywoływać `PrepareEditCtrl` dla wszystkie formanty, dla których są wymiany danych za pomocą DDX lub Sprawdzanie poprawności danych za pośrednictwem DDV edycji.  
  
 Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [26 Uwaga techniczna](../../mfc/tn026-ddx-and-ddv-routines.md). Omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md) i [tematy — okno dialogowe](../../mfc/dialog-boxes.md).  
  
##  <a name="prepareolectrl"></a>CDataExchange::PrepareOleCtrl  
 Struktura wywołuje tę funkcję elementu członkowskiego, aby przygotować określony formant OLE wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV).  
  
```  
COleControlSite* PrepareOleCtrl(int nIDC);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDC`  
 Identyfikator formantu OLE można przygotować DDX i DDV.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do lokacji formantu OLE.  
  
### <a name="remarks"></a>Uwagi  
 Użyj [PrepareEditCtrl](#prepareeditctrl) zamiast tego dla formantów edycyjnych lub [PrepareCtrl](#preparectrl) dla innych formantów innych niż OLE.  
  
 Implementors niestandardowe procedury DDX i DDV powinny wywoływać `PrepareOleCtrl` dla wszystkich kontrolek OLE, dla których są wymiany danych za pomocą DDX lub Sprawdzanie poprawności danych za pośrednictwem DDV.  
  
 Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [26 Uwaga techniczna](../../mfc/tn026-ddx-and-ddv-routines.md). Omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i weryfikacja](../../mfc/dialog-data-exchange-and-validation.md) i [tematy — okno dialogowe](../../mfc/dialog-boxes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC VIEWEX](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)   
 [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)

