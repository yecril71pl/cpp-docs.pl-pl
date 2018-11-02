---
title: Cdataexchange — klasa
ms.date: 11/04/2016
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
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
ms.openlocfilehash: 7d0a804294fa5da619bdab4184adf3e28c420506
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509296"
---
# <a name="cdataexchange-class"></a>Cdataexchange — klasa

Obsługuje wymiana danych okna dialogowego (DDX) i procedury sprawdzania poprawności (DDV) danych okna dialogowego używane przez klasy Microsoft Foundation.

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
|[CDataExchange::Fail](#fail)|Wywołuje się, gdy weryfikacja nie powiedzie się. Przywraca poprzedni formant fokus i zgłasza wyjątek.|
|[CDataExchange::PrepareCtrl](#preparectrl)|Przygotowuje określoną kontrolkę do wymiany danych lub sprawdzania poprawności. Na użytek nonedit kontrolki.|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Przygotowuje kontrolki edycji określony do wymiany danych lub sprawdzania poprawności.|
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Przygotowuje określoną kontrolkę OLE do wymiany danych lub sprawdzania poprawności. Na użytek nonedit kontrolki.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Flaga kierunku DDX i DDV.|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|Okno dialogowe lub okna, w którym wymiany danych odbywa się.|

## <a name="remarks"></a>Uwagi

`CDataExchange` nie ma klasy bazowej.

Klasa jest używana podczas pisania procedury wymiany danych dla niestandardowych typów danych lub kontrolki, lub jeśli piszesz własnego procedury walidacji danych. Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [techniczne 26 Uwaga](../../mfc/tn026-ddx-and-ddv-routines.md). Aby uzyskać omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md) i [okna dialogowe](../../mfc/dialog-boxes.md).

A `CDataExchange` obiekt zawiera informacje kontekstowe potrzebne do podjęcia DDX i DDV umieścić. Flaga *m_bSaveAndValidate* ma wartość FAŁSZ, gdy DDX jest używany do wypełniania wartości początkowe formantów okna dialogowego z elementów członkowskich danych. Flaga *m_bSaveAndValidate* ma wartość TRUE, gdy DDX jest używana do ustawiania bieżące wartości formantów okna dialogowego do elementów członkowskich danych i kiedy DDV służy do sprawdzania wartości danych. W przypadku niepowodzenia weryfikacji DDV procedury DDV wyświetli okno komunikatu, wyjaśniające, błąd danych wejściowych. Następnie wywoła procedurę DDV `Fail` zresetować fokus do problematycznych kontroli i zgłosić wyjątek, aby zatrzymać proces sprawdzania poprawności.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDataExchange`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="cdataexchange"></a>  CDataExchange::CDataExchange

Wywołaj tę funkcję elementu członkowskiego do konstruowania `CDataExchange` obiektu.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>Parametry

*pDlgWnd*<br/>
Wskaźnik do okna nadrzędnego, który zawiera formant. Zazwyczaj jest to [CDialog](../../mfc/reference/cdialog-class.md)-pochodnych obiektu.

*bSaveAndValidate*<br/>
W przypadku opcji TRUE tego obiektu sprawdza poprawność danych, a następnie zapisuje dane z formantów do elementów członkowskich. W przypadku wartości FAŁSZ tego obiektu przenoszenie danych z elementów członkowskich do kontrolek.

### <a name="remarks"></a>Uwagi

Konstruowania `CDataExchange` obiektu samodzielnie do przechowywania dodatkowych informacji w obiekcie wymiany danych do przekazania do swojej okna [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

##  <a name="fail"></a>  CDataExchange::Fail

Struktura wywołuje tej funkcji elementu członkowskiego w przypadku niepowodzenia operacji sprawdzania poprawności (DDV) danych okna dialogowego.

```
void Fail();
```

### <a name="remarks"></a>Uwagi

`Fail` Przywraca fokus i wyboru do kontrolki, których Weryfikacja nie powiodła się, (jeśli istnieje formantu do przywrócenia). `Fail` następnie zgłasza wyjątek typu [CUserException](../../mfc/reference/cuserexception-class.md) można zatrzymać procesu sprawdzania poprawności. Wyjątek powoduje, że okno komunikatu, wyjaśniające, błędów, które mają być wyświetlane. Po weryfikacji DDV zakończy się niepowodzeniem, użytkownik może ponownie danych w formancie powodujący problemy.

Można wywołać implementors niestandardowe procedury DDV `Fail` z ich procedury w przypadku niepowodzenia weryfikacji.

Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [techniczne 26 Uwaga](../../mfc/tn026-ddx-and-ddv-routines.md). Aby uzyskać omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md) i [tematy okno dialogowe](../../mfc/dialog-boxes.md).

##  <a name="m_bsaveandvalidate"></a>  CDataExchange::m_bSaveAndValidate

Ta flaga wskazuje kierunek operacji programu exchange (DDX) danych okna dialogowego.

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Uwagi

Flaga jest różna od zera jeśli `CDataExchange` obiektu jest używana do przenoszenia danych z formantów okna dialogowego do elementów członkowskich danych klasy okien dialogowych, po użytkownik edytuje kontrolki. Flaga wynosi zero, jeśli obiekt jest używany do zainicjowania formantów okna dialogowego z elementów członkowskich danych klasy okien dialogowych.

Flagi również jest różna od zera podczas walidacji danych okna dialogowego (DDV).

Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [techniczne 26 Uwaga](../../mfc/tn026-ddx-and-ddv-routines.md). Aby uzyskać omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md) i [tematy okno dialogowe](../../mfc/dialog-boxes.md).

##  <a name="m_pdlgwnd"></a>  CDataExchange::m_pDlgWnd

Zawiera wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiektu, dla których okna dialogowego wymiany danych (DDX) lub sprawdzania poprawności (DDV) odbywa się.

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Uwagi

Ten obiekt jest zwykle [CDialog](../../mfc/reference/cdialog-class.md) obiektu. Implementors niestandardowe procedury DDX i DDV za pomocą tego wskaźnika można uzyskać dostęp do okna dialogowego, który zawiera formanty działają na.

Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [techniczne 26 Uwaga](../../mfc/tn026-ddx-and-ddv-routines.md). Aby uzyskać omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md) i [tematy okno dialogowe](../../mfc/dialog-boxes.md).

##  <a name="preparectrl"></a>  CDataExchange::PrepareCtrl

Struktura wywołuje tę funkcję elementu członkowskiego, aby przygotować określoną kontrolkę wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV).

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC*<br/>
Identyfikator kontrolki mają zostać przygotowane do DDX i DDV.

### <a name="return-value"></a>Wartość zwracana

HWND kontrolki przygotowywane dla DDX i DDV.

### <a name="remarks"></a>Uwagi

Użyj [PrepareEditCtrl](#prepareeditctrl) dla formantów edycji; używają tej funkcji elementu członkowskiego dla wszystkich innych kontrolek.

Przygotowanie składa się z przechowywaniem HWND formantu w `CDataExchange` klasy. Struktura używa tego dojścia do przywrócenia fokus do wcześniej ukierunkowanych kontroli awarii DDX i DDV.

Należy wywołać implementors niestandardowe procedury DDX i DDV `PrepareCtrl` dla wszystkich kontrolek bez edycji, dla których są wymiana danych za pomocą DDX lub Sprawdzanie poprawności danych za pośrednictwem DDV.

Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [techniczne 26 Uwaga](../../mfc/tn026-ddx-and-ddv-routines.md). Aby uzyskać omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md) i [tematy okno dialogowe](../../mfc/dialog-boxes.md).

##  <a name="prepareeditctrl"></a>  CDataExchange::PrepareEditCtrl

Struktura wywołuje tę funkcję elementu członkowskiego, aby przygotować kontrolki edycji określonego wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV).

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC*<br/>
Identyfikator formantu edycji należy przygotować DDX i DDV.

### <a name="return-value"></a>Wartość zwracana

HWND przygotowywane dla DDX i DDV kontrolki edycji.

### <a name="remarks"></a>Uwagi

Użyj [PrepareCtrl](#preparectrl) zamiast dla wszystkich kontrolek bez edycji.

Przygotowanie składa się z dwóch kwestii. Po pierwsze, `PrepareEditCtrl` przechowuje HWND formantu w `CDataExchange` klasy. Struktura używa tego dojścia do przywrócenia fokus do wcześniej ukierunkowanych kontroli awarii DDX i DDV. Drugi `PrepareEditCtrl` ustawia flagę w `CDataExchange` klasy w celu wskazania, że formant, którego dane jest wymieniana lub sprawdzania poprawności jest formant edycji.

Należy wywołać implementors niestandardowe procedury DDX i DDV `PrepareEditCtrl` dla wszystkich edycji wzbogaconej, dla których są wymiana danych za pomocą DDX lub Sprawdzanie poprawności danych za pośrednictwem DDV.

Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [techniczne 26 Uwaga](../../mfc/tn026-ddx-and-ddv-routines.md). Aby uzyskać omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md) i [tematy okno dialogowe](../../mfc/dialog-boxes.md).

##  <a name="prepareolectrl"></a>  CDataExchange::PrepareOleCtrl

Struktura wywołuje tę funkcję elementu członkowskiego, aby przygotować określoną kontrolkę OLE wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV).

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC*<br/>
Identyfikator kontrolki OLE mają zostać przygotowane do DDX i DDV.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do lokacji sterowania OLE.

### <a name="remarks"></a>Uwagi

Użyj [PrepareEditCtrl](#prepareeditctrl) zamiast dla formantów edycji lub [PrepareCtrl](#preparectrl) dla wszystkich kontrolek / OLE.

Należy wywołać implementors niestandardowe procedury DDX i DDV `PrepareOleCtrl` dla wszystkich kontrolek OLE, dla których są wymiana danych za pomocą DDX lub Sprawdzanie poprawności danych za pośrednictwem DDV.

Aby uzyskać więcej informacji na temat pisania własnych procedury DDX i DDV, zobacz [techniczne 26 Uwaga](../../mfc/tn026-ddx-and-ddv-routines.md). Aby uzyskać omówienie DDX i DDV, zobacz [wymiana danych okna dialogowego i sprawdzanie poprawności](../../mfc/dialog-data-exchange-and-validation.md) i [tematy okno dialogowe](../../mfc/dialog-boxes.md).

## <a name="see-also"></a>Zobacz też

[Próbki MFC VIEWEX](../../visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)

