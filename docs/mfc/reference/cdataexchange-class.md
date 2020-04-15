---
title: Klasa CDataExchange
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
ms.openlocfilehash: 73319ad898bfebf4caf191954ebb3935bd4ebce9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321963"
---
# <a name="cdataexchange-class"></a>Klasa CDataExchange

Obsługuje procedury wymiany danych w oknie dialogowym (DDX) i sprawdzania poprawności danych okna dialogowego (DDV) używane przez klasy Microsoft Foundation.

## <a name="syntax"></a>Składnia

```
class CDataExchange
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDataExchange::CDataExchange](#cdataexchange)|Konstruuje `CDataExchange` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDataExchange::Niepowodzenie](#fail)|Wywoływane, gdy sprawdzanie poprawności nie powiedzie się. Resetuje fokus do poprzedniego formantu i zgłasza wyjątek.|
|[CDataExchange::PrepareCtrl](#preparectrl)|Przygotowuje określony formant do wymiany danych lub sprawdzania poprawności. Służy do kontroli nonedit.|
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|Przygotowuje określony formant edycji do wymiany lub sprawdzania poprawności danych.|
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|Przygotowuje określony formant OLE do wymiany lub sprawdzania poprawności danych. Służy do kontroli nonedit.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|Flaga dla kierunku DDX i DDV.|
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|Okno dialogowe lub okno, w którym odbywa się wymiana danych.|

## <a name="remarks"></a>Uwagi

`CDataExchange`nie ma klasy podstawowej.

Tej klasy należy używać, jeśli piszesz procedury wymiany danych dla niestandardowych typów danych lub formantów lub jeśli piszesz własne procedury sprawdzania poprawności danych. Aby uzyskać więcej informacji na temat pisania własnych procedur DDX i DDV, zobacz [Uwaga techniczna 26](../../mfc/tn026-ddx-and-ddv-routines.md). Aby zapoznać się z omówieniem ddx i DDV, zobacz [Okno dialogowe Wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md) oraz okna [dialogowe](../../mfc/dialog-boxes.md).

Obiekt `CDataExchange` zawiera informacje kontekstu potrzebne dla DDX i DDV odbywać. Flaga *m_bSaveAndValidate* jest FALSE, gdy DDX jest używany do wypełniania wartości początkowych formantów okna dialogowego z elementów członkowskich danych. Flaga *m_bSaveAndValidate* jest TRUE, gdy DDX jest używany do ustawiania bieżących wartości formantów okna dialogowego do elementów członkowskich danych i gdy DDV jest używany do sprawdzania poprawności wartości danych. Jeśli sprawdzanie poprawności DDV nie powiedzie się, procedura DDV wyświetli okno komunikatu wyjaśniające błąd wejściowy. Procedura DDV następnie `Fail` wywoła, aby zresetować fokus do kontroli naruszającej i zgłosić wyjątek, aby zatrzymać proces sprawdzania poprawności.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDataExchange`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="cdataexchangecdataexchange"></a><a name="cdataexchange"></a>CDataExchange::CDataExchange

Wywołanie tej funkcji `CDataExchange` elementu członkowskiego do konstruowania obiektu.

```
CDataExchange(
    CWnd* pDlgWnd,
    BOOL bSaveAndValidate);
```

### <a name="parameters"></a>Parametry

*pDlgWnd (właśc.*<br/>
Wskaźnik do okna nadrzędnego, który zawiera formant. Zazwyczaj jest to [obiekt CDialog](../../mfc/reference/cdialog-class.md)-pochodna.

*bSaveAndValidate*<br/>
Jeśli TRUE, ten obiekt sprawdza poprawność danych, a następnie zapisuje dane z formantów do członków. Jeśli FALSE, ten obiekt przeniesie dane z elementów członkowskich do formantów.

### <a name="remarks"></a>Uwagi

Skonstruuj `CDataExchange` obiekt samodzielnie do przechowywania dodatkowych informacji w obiekcie wymiany danych, aby przekazać do funkcji członkowskiej [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange) okna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]

## <a name="cdataexchangefail"></a><a name="fail"></a>CDataExchange::Niepowodzenie

Struktura wywołuje tę funkcję elementu członkowskiego, gdy operacja sprawdzania poprawności danych okna dialogowego (DDV) kończy się niepowodzeniem.

```
void Fail();
```

### <a name="remarks"></a>Uwagi

`Fail`przywraca fokus i zaznaczenie do formantu, którego sprawdzanie poprawności nie powiodło się (jeśli istnieje formant do przywrócenia). `Fail`następnie zgłasza wyjątek typu [CUserException,](../../mfc/reference/cuserexception-class.md) aby zatrzymać proces sprawdzania poprawności. Wyjątek powoduje, że okno komunikatu wyjaśniające błąd, który ma być wyświetlany. Po zakończeniu sprawdzania poprawności DDV użytkownik może ponownie wcielić dane w formancie naruszającym przepisy.

Implementatory niestandardowych procedur DDV `Fail` można wywołać z ich procedur, gdy sprawdzanie poprawności nie powiedzie się.

Aby uzyskać więcej informacji na temat pisania własnych procedur DDX i DDV, zobacz [Uwaga techniczna 26](../../mfc/tn026-ddx-and-ddv-routines.md). Aby zapoznać się z omówieniem DDX i DDV, zobacz [Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md) oraz tematy okna [dialogowego](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_bsaveandvalidate"></a><a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate

Ta flaga wskazuje kierunek operacji wymiany danych dialogowych (DDX).

```
BOOL m_bSaveAndValidate;
```

### <a name="remarks"></a>Uwagi

Flaga jest niezerowa, `CDataExchange` jeśli obiekt jest używany do przenoszenia danych z formantów okna dialogowego do elementów członkowskich danych klasy dialogowej po edycji formantów przez użytkownika. Flaga wynosi zero, jeśli obiekt jest używany do inicjowania formantów okna dialogowego z elementów członkowskich danych klasy dialogowej.

Flaga jest również niezerowa podczas sprawdzania poprawności danych okna dialogowego (DDV).

Aby uzyskać więcej informacji na temat pisania własnych procedur DDX i DDV, zobacz [Uwaga techniczna 26](../../mfc/tn026-ddx-and-ddv-routines.md). Aby zapoznać się z omówieniem DDX i DDV, zobacz [Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md) oraz tematy okna [dialogowego](../../mfc/dialog-boxes.md).

## <a name="cdataexchangem_pdlgwnd"></a><a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd

Zawiera wskaźnik do obiektu [CWnd,](../../mfc/reference/cwnd-class.md) dla którego odbywa się wymiana danych dialogowych (DDX) lub sprawdzanie poprawności (DDV).

```
CWnd* m_pDlgWnd;
```

### <a name="remarks"></a>Uwagi

Ten obiekt jest zwykle [CDialog](../../mfc/reference/cdialog-class.md) obiektu. Implementatory niestandardowych procedur DDX lub DDV można użyć tego wskaźnika, aby uzyskać dostęp do okna dialogowego, który zawiera formanty, które działają na.

Aby uzyskać więcej informacji na temat pisania własnych procedur DDX i DDV, zobacz [Uwaga techniczna 26](../../mfc/tn026-ddx-and-ddv-routines.md). Aby zapoznać się z omówieniem DDX i DDV, zobacz [Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md) oraz tematy okna [dialogowego](../../mfc/dialog-boxes.md).

## <a name="cdataexchangepreparectrl"></a><a name="preparectrl"></a>CDataExchange::PrepareCtrl

Struktura wywołuje tę funkcję elementu członkowskiego, aby przygotować określony formant do wymiany danych okna dialogowego (DDX) i sprawdzania poprawności (DDV).

```
HWND PrepareCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC (nIDC)*<br/>
Identyfikator formantu, który ma być przygotowany dla DDX lub DDV.

### <a name="return-value"></a>Wartość zwracana

HWND sterownika przygotowywanego dla DDX lub DDV.

### <a name="remarks"></a>Uwagi

Zamiast tego [użyj funkcji PrepareEditCtrl](#prepareeditctrl) do edycji formantów; użyj tej funkcji elementu członkowskiego dla wszystkich innych formantów.

Przygotowanie polega na przechowywaniu hwnd formantu w `CDataExchange` klasie. Struktura używa tego dojścia, aby przywrócić fokus do wcześniej skoncentrowanego formantu w przypadku awarii DDX lub DDV.

Implementatory niestandardowych procedur DDX lub DDV powinny wymagać `PrepareCtrl` wszystkich formantów nieedytujących, dla których wymieniają dane za pośrednictwem DDX lub weryfikują dane za pośrednictwem DDV.

Aby uzyskać więcej informacji na temat pisania własnych procedur DDX i DDV, zobacz [Uwaga techniczna 26](../../mfc/tn026-ddx-and-ddv-routines.md). Aby zapoznać się z omówieniem DDX i DDV, zobacz [Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md) oraz tematy okna [dialogowego](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareeditctrl"></a><a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl

Struktura wywołuje tę funkcję elementu członkowskiego, aby przygotować określony formant edycji do wymiany danych okna dialogowego (DDX) i sprawdzania poprawności (DDV).

```
HWND PrepareEditCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC (nIDC)*<br/>
Identyfikator formantu edycji, który ma być przygotowany dla DDX lub DDV.

### <a name="return-value"></a>Wartość zwracana

HWND formantu edycji przygotowywane dla DDX lub DDV.

### <a name="remarks"></a>Uwagi

Użyj [PrepareCtrl](#preparectrl) zamiast dla wszystkich formantów nie edycji.

Przygotowanie składa się z dwóch rzeczy. Po `PrepareEditCtrl` pierwsze przechowuje hwnd formantu w `CDataExchange` klasie. Struktura używa tego dojścia, aby przywrócić fokus do wcześniej skoncentrowanego formantu w przypadku awarii DDX lub DDV. Po `PrepareEditCtrl` drugie ustawia flagę w `CDataExchange` klasie, aby wskazać, że formant, którego dane są wymieniane lub sprawdzane jest formant edycji.

Implementatory niestandardowych procedur DDX lub DDV powinny wymagać `PrepareEditCtrl` wszystkich formantów edycji, dla których wymieniają dane za pośrednictwem DDX lub sprawdzania poprawności danych za pośrednictwem DDV.

Aby uzyskać więcej informacji na temat pisania własnych procedur DDX i DDV, zobacz [Uwaga techniczna 26](../../mfc/tn026-ddx-and-ddv-routines.md). Aby zapoznać się z omówieniem DDX i DDV, zobacz [Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md) oraz tematy okna [dialogowego](../../mfc/dialog-boxes.md).

## <a name="cdataexchangeprepareolectrl"></a><a name="prepareolectrl"></a>CDataExchange::PrepareOleCtrl

Struktura wywołuje tę funkcję elementu członkowskiego, aby przygotować określony formant OLE do wymiany danych okna dialogowego (DDX) i sprawdzania poprawności (DDV).

```
COleControlSite* PrepareOleCtrl(int nIDC);
```

### <a name="parameters"></a>Parametry

*nIDC (nIDC)*<br/>
Identyfikator formantu OLE, który ma być przygotowany dla DDX lub DDV.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do witryny sterowania OLE.

### <a name="remarks"></a>Uwagi

Zamiast tego należy użyć [funkcji PrepareEditCtrl](#prepareeditctrl) do edycji formantów lub [PrepareCtrl](#preparectrl) dla wszystkich innych formantów innych niż OLE.

Implementatory niestandardowych procedur DDX lub DDV powinny wymagać `PrepareOleCtrl` wszystkich formantów OLE, dla których wymieniają dane za pośrednictwem DDX lub sprawdzania poprawności danych za pośrednictwem DDV.

Aby uzyskać więcej informacji na temat pisania własnych procedur DDX i DDV, zobacz [Uwaga techniczna 26](../../mfc/tn026-ddx-and-ddv-routines.md). Aby zapoznać się z omówieniem DDX i DDV, zobacz [Dialog wymiany danych i sprawdzania poprawności](../../mfc/dialog-data-exchange-and-validation.md) oraz tematy okna [dialogowego](../../mfc/dialog-boxes.md).

## <a name="see-also"></a>Zobacz też

[Przykładowy viewex MFC](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)<br/>
[CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)
