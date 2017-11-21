---
title: "Cdatetimectrl — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
dev_langs: C++
helpviewer_keywords:
- CDateTimeCtrl [MFC], CDateTimeCtrl
- CDateTimeCtrl [MFC], CloseMonthCal
- CDateTimeCtrl [MFC], Create
- CDateTimeCtrl [MFC], GetDateTimePickerInfo
- CDateTimeCtrl [MFC], GetIdealSize
- CDateTimeCtrl [MFC], GetMonthCalColor
- CDateTimeCtrl [MFC], GetMonthCalCtrl
- CDateTimeCtrl [MFC], GetMonthCalFont
- CDateTimeCtrl [MFC], GetMonthCalStyle
- CDateTimeCtrl [MFC], GetRange
- CDateTimeCtrl [MFC], GetTime
- CDateTimeCtrl [MFC], SetFormat
- CDateTimeCtrl [MFC], SetMonthCalColor
- CDateTimeCtrl [MFC], SetMonthCalFont
- CDateTimeCtrl [MFC], SetMonthCalStyle
- CDateTimeCtrl [MFC], SetRange
- CDateTimeCtrl [MFC], SetTime
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ced7bfbb2cedd8cad4353cdbb2d5627864de5ad7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdatetimectrl-class"></a>Cdatetimectrl — klasa
Hermetyzuje funkcjonalność formant wyboru daty i godziny.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDateTimeCtrl : public CWnd  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Konstruuje `CDateTimeCtrl` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Zamyka bieżący formant selektora daty i godziny.|  
|[CDateTimeCtrl::Create](#create)|Tworzy formant wyboru daty i godziny i dołącza go do `CDateTimeCtrl` obiektu.|  
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Pobiera informacje o bieżącym formant wyboru daty i godziny.|  
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Zwraca rozmiar idealny formantu selektora daty i godziny, który jest wymagany, aby wyświetlić bieżącą datę lub godzinę.|  
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Pobiera kolor dla danej części kalendarza miesięcznego w formancie selektora daty i godziny.|  
|[CDateTimeCtrl::GetMonthCalCtrl](#getmonthcalctrl)|Pobiera `CMonthCalCtrl` obiekt skojarzony z formant wyboru daty i godziny.|  
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Pobiera czcionkę używaną obecnie przez datę i formant kalendarza miesięcznego podrzędnych formant wyboru godziny.|  
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Pobiera styl bieżący formant selektora daty i godziny.|  
|[CDateTimeCtrl::GetRange](#getrange)|Pobiera bieżący minimalne i maksymalne dozwolone czasy systemowe w formancie selektora daty i godziny.|  
|[CDateTimeCtrl::GetTime](#gettime)|Pobiera obecnie wybrana wartość czasu z formant wyboru daty i godziny i umieszczenie go w określonym `SYSTEMTIME` struktury.|  
|[CDateTimeCtrl::SetFormat](#setformat)|Określa wyświetlanie formantu selektora daty i godziny zgodnie z danego formatu ciągu.|  
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Ustawia kolor dla danej części kalendarza miesięcznego w formancie selektora daty i godziny.|  
|[CDateTimeCtrl::SetMonthCalFont](#setmonthcalfont)|Ustawia czcionkę, który będzie używany przez formant kalendarza miesięcznego podrzędnych Data i godzina selektora formantu.|  
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Ustawia styl bieżący formant selektora daty i godziny.|  
|[CDateTimeCtrl::SetRange](#setrange)|Ustawia czas minimalne i maksymalne dozwolone systemu dla formant wyboru daty i godziny.|  
|[CDateTimeCtrl::SetTime](#settime)|Ustawia czas w formancie selektora daty i godziny.|  
  
## <a name="remarks"></a>Uwagi  
 Formant selektora daty i godziny (odwołania kontrolki DTP) udostępnia prosty interfejs do wymiany informacji daty i godziny z użytkownikiem. Ten interfejs zawiera pola, z których każdy zawiera część daty i godziny informacje przechowywane w formancie. Użytkownik może zmienić informacje przechowywane w formancie, zmieniając zawartości ciągu w danym polu. Użytkownik może przenieść do innego pola przy użyciu myszy lub klawiatury.  
  
 Formant selektora daty i godziny można dostosować przez zastosowanie różnych stylów do obiektu po jego utworzeniu. Zobacz [style daty i godziny selektora kontroli](http://msdn.microsoft.com/library/windows/desktop/bb761728) w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat style właściwe dla formant wyboru daty i godziny. Można określić format wyświetlania kontrolki DTP przy użyciu stylów formatowania. Te style formatu są opisane w obszarze "Format style" w temacie Windows SDK [style daty i godziny selektora kontroli](http://msdn.microsoft.com/library/windows/desktop/bb761728).  
  
 Formant selektora daty i godziny używa również powiadomień i wywołania zwrotne, które zostały opisane w [przy użyciu CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDateTimeCtrl`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdtctl.h  
  
##  <a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl  
 Konstruuje `CDateTimeCtrl` obiektu.  
  
```  
CDateTimeCtrl();
```  
  
##  <a name="closemonthcal"></a>CDateTimeCtrl::CloseMonthCal  
 Zamyka bieżący formant selektora daty i godziny.  
  
```  
void CloseMonthCal() const;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [DTM_CLOSEMONTHCAL](http://msdn.microsoft.com/library/windows/desktop/bb761753) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_dateTimeCtrl`, która jest używana do uzyskania programowego dostępu do formant wyboru daty i godziny. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu zamyka listy rozwijanej kalendarza dla bieżącego formant wyboru daty i godziny.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]  
  
##  <a name="create"></a>CDateTimeCtrl::Create  
 Tworzy formant wyboru daty i godziny i dołącza go do `CDateTimeCtrl` obiektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Określa kombinację stylów formantu czasu daty. Zobacz [style daty i godziny selektora kontroli](http://msdn.microsoft.com/library/windows/desktop/bb761728) w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat style selektora daty i godziny.  
  
 `rect`  
 Odwołanie do [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktury, która jest położenie i rozmiar formant wyboru daty i godziny.  
  
 `pParentWnd`  
 Wskaźnik do [CWnd](../../mfc/reference/cwnd-class.md) obiekt, który jest okno nadrzędne formant wyboru daty i godziny. Nie może być **NULL**.  
  
 `nID`  
 Określa identyfikator formantu Data i godzina selektora formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
  
##### <a name="to-create-a-date-and-time-picker-control"></a>Aby utworzyć formant wyboru daty i godziny  
  
1.  Wywołanie [CDateTimeCtrl](#cdatetimectrl) do skonstruowania `CDateTimeCtrl` obiektu.  
  
2.  Wywołanie tej funkcji elementu członkowskiego, który tworzy formant wyboru daty i godziny systemu Windows i dołącza go do `CDateTimeCtrl` obiektu.  
  
 Podczas wywoływania **Utwórz**, są inicjowane wspólne kontrolki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]  
  
##  <a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo  
 Pobiera informacje o bieżącym formant wyboru daty i godziny.  
  
```   
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out]`pDateTimePickerInfo`|Wskaźnik do [DATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761729) struktury, który odbiera opis bieżący formant selektora daty i godziny.<br /><br /> Element wywołujący jest odpowiedzialny za przydzielanie tej struktury. Jednak ta metoda inicjuje `cbSize` elementu członkowskiego struktury.|  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli ta metoda zakończy się pomyślnie; w przeciwnym razie `false`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [DTM_GETDATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761755) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_dateTimeCtrl`, która jest używana do uzyskania programowego dostępu do formant wyboru daty i godziny. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu Określa, czy pomyślnie pobiera informacje o bieżącym formant wyboru daty i godziny.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]  
  
##  <a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor  
 Pobiera kolor dla danej części kalendarza miesięcznego w formancie selektora daty i godziny.  
  
```  
COLORREF GetMonthCalColor(int iColor) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `iColor`  
 `int` Wartość określającą, jaki obszar kolor kalendarza miesięcznego można pobrać. Aby uzyskać listę wartości, zobacz `iColor` parametr [SetMonthCalColor](#setmonthcalcolor).  
  
### <a name="return-value"></a>Wartość zwracana  
 A **COLORREF** wartość, która reprezentuje kolor ustawienie określoną część formant kalendarza miesięcznego w przypadku powodzenia. Funkcja zwraca wartość -1 w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [DTM_GETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761759), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]  
  
##  <a name="getmonthcalctrl"></a>CDateTimeCtrl::GetMonthCalCtrl  
 Pobiera `CMonthCalCtrl` obiekt skojarzony z formant wyboru daty i godziny.  
  
```  
CMonthCalCtrl* GetMonthCalCtrl() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) obiekt, lub **NULL** w przypadku niepowodzenia lub jeśli okno nie jest widoczna.  
  
### <a name="remarks"></a>Uwagi  
 Formant selektora daty i godziny tworzenia formancie kalendarza miesięcznego podrzędnych, gdy użytkownik kliknie strzałkę listy rozwijanej. Gdy `CMonthCalCtrl` obiektu nie jest już potrzebny, został zniszczony, więc aplikacja nie należy polegać na przechowywanie obiekt reprezentujący kalendarza miesięcznego podrzędnych formant wyboru godziny daty.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]  
  
##  <a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont  
 Pobiera czcionkę używaną obecnie przez datę i formant kalendarza miesięcznego formant wyboru godziny.  
  
```  
CFont* GetMonthCalFont() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [cfont —](../../mfc/reference/cfont-class.md) obiekt, lub **NULL** w przypadku niepowodzenia.  
  
### <a name="remarks"></a>Uwagi  
 `CFont` Obiekt wskazywany przez wartość zwracana jest obiektem tymczasowym i zostanie zniszczony podczas następnego przetwarzania bezczynności.  
  
##  <a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle  
 Pobiera styl formant kalendarza miesięcznego listy rozwijanej, która jest skojarzona z bieżącym formant wyboru daty i godziny.  
  
```  
DWORD GetMonthCalStyle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Styl formantu kalendarza miesięcznego listy rozwijanej jest bitowe połączenie lub stylów formantu selektora daty i godziny. Aby uzyskać więcej informacji, zobacz [stylów formantu kalendarza miesięcznego](http://msdn.microsoft.com/library/windows/desktop/bb760919).  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [DTM_GETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761763) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
##  <a name="getrange"></a>CDateTimeCtrl::GetRange  
 Pobiera bieżący minimalne i maksymalne dozwolone czasy systemowe w formancie selektora daty i godziny.  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `pMinRange`  
 Wskaźnik do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu lub [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiekt zawierający najwcześniejszym terminie w `CDateTimeCtrl` obiektu.  
  
 `pMaxRange`  
 Wskaźnik do `COleDateTime` obiektu lub `CTime` obiekt zawierający Najpóźniejsza godzina dozwolone w `CDateTimeCtrl` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `DWORD` wartość zawierającą flagi wskazujące zakresy, które są ustawione. IF  
  
 `return value & GDTR_MAX` == 0  
  
 drugi parametr jest nieprawidłowy. Podobnie jeśli  
  
 `return value & GDTR_MIN` == 0  
  
 pierwszy parametr jest nieprawidłowy.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [DTM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761767), zgodnie z opisem w zestawie Windows SDK. W implementacji MFC, można określić albo `COleDateTime` lub `CTime` użycia.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#4](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]  
  
##  <a name="gettime"></a>CDateTimeCtrl::GetTime  
 Pobiera obecnie wybrana wartość czasu z formant wyboru daty i godziny i umieszczenie go w określonym `SYSTEMTIME` struktury.  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;  
DWORD GetTime(CTime& timeDest) const;  
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *timeDest*  
 W pierwszej wersji odwołania do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt, który otrzyma dotyczących czasu systemowego. W drugiej wersji odwołania do [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiekt, który otrzyma dotyczących czasu systemowego.  
  
 *pTimeDest*  
 Wskaźnik do [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury otrzymywanie informacji czasu systemu. Nie może być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 W pierwszej wersji różną od zera, jeśli pomyślnie zapisane czas `COleDateTime` obiektu; w przeciwnym razie 0. W wersjach drugiego i trzeciego `DWORD` wartość równą **dwFlag** zestaw elementów członkowskich [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) struktury. Zobacz **uwagi** sekcji poniżej, aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [DTM_GETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761769), zgodnie z opisem w zestawie Windows SDK. W implementacji MFC **GetTime**, można użyć `COleDateTime` lub `CTime` klas, lub użyć `SYSTEMTIME` struktury do przechowywania informacji o czasie.  
  
 Wartość zwracana `DWORD` w wersjach drugiego i trzeciego powyżej, wskazuje, czy formant wyboru daty i godziny jest ustawiona na stan "Brak daty" wskazane [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) element członkowski struktury `dwFlags`. Jeśli wartość zwracana równa **GDT_NONE**, formantu ma ustawioną wartość "Brak daty" stan i używa **DTS_SHOWNONE** stylu. Jeśli wartość zwracana równa **GDT_VALID**, czas systemowy pomyślnie są przechowywane w lokalizacji docelowej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]  
  
##  <a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize  
 Zwraca rozmiar idealny formantu selektora daty i godziny, który jest wymagany, aby wyświetlić bieżącą datę lub godzinę.  
  
```  
BOOL GetIdealSize(LPSIZE psize) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[out]`psize`|Wskaźnik do [rozmiar](http://msdn.microsoft.com/library/windows/desktop/dd145106) strukturę, która zawiera rozmiar idealny dla formantu.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwracana wartość jest zawsze `true`.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [DTM_GETIDEALSIZE](http://msdn.microsoft.com/library/windows/desktop/bb761757) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_dateTimeCtrl`, która jest używana do uzyskania programowego dostępu do formant wyboru daty i godziny. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod pobiera rozmiar idealny, aby wyświetlić formant wyboru daty i godziny.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]  
  
##  <a name="setformat"></a>CDateTimeCtrl::SetFormat  
 Określa wyświetlanie formantu selektora daty i godziny zgodnie z danego formatu ciągu.  
  
```  
BOOL SetFormat(LPCTSTR pstrFormat);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrFormat*  
 Wskaźnik do ciągu formatu zakończony zerem, który definiuje żądane. Ustawienie tego parametru **NULL** przywróci domyślny ciąg formatu w celu bieżący styl formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
> [!NOTE]
>  Dane wejściowe użytkownika nie określa powodzenie lub Niepowodzenie dla tego wywołania.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [DTM_SETFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb761771), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#6](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]  
  
##  <a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor  
 Ustawia kolor dla danej części kalendarza miesięcznego w formancie selektora daty i godziny.  
  
```  
COLORREF SetMonthCalColor(
    int iColor,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>Parametry  
 `iColor`  
 `int`Określanie obszar formant kalendarza miesięcznego można ustawić wartości. Ta wartość może być jedną z następujących czynności.  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|MCSC_BACKGROUND|Kolor tła wyświetlany miesięcy.|  
|MCSC_MONTHBK|Kolor tła wyświetlany w ciągu miesiąca.|  
|MCSC_TEXT|Kolor używany do wyświetlania tekstu w ciągu miesiąca.|  
|MCSC_TITLEBK|Kolor tła wyświetlany w tytule kalendarza.|  
|MCSC_TITLETEXT|Kolor używany do wyświetlania tekstu w tytule kalendarza.|  
|MCSC_TRAILINGTEXT|Kolor używany do wyświetlania nagłówka i końcowy dzień tekstu. Dni poprzedzające i następujące to dni poprzedniego i następnego miesiąca pojawiające się na bieżącego kalendarza.|  
  
 `ref`  
 A **COLORREF** wartość reprezentującą kolor, który zostanie ustawiona dla określonego obszaru kalendarza miesięcznego.  
  
### <a name="return-value"></a>Wartość zwracana  
 A **COLORREF** wartość, która reprezentuje poprzedniego ustawienia kolorów dla określonej części formant kalendarza miesięcznego w przypadku powodzenia. W przeciwnym razie komunikat zwraca -1.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [DTM_SETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761773), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).  
  
##  <a name="setmonthcalfont"></a>CDateTimeCtrl::SetMonthCalFont  
 Ustawia czcionkę, który będzie używany przez formant kalendarza miesięcznego podrzędnych Data i godzina selektora formantu.  
  
```  
void SetMonthCalFont(
    HFONT hFont,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `hFont`  
 Dojście do czcionki, która zostanie ustawiona.  
  
 `bRedraw`  
 Określa, czy formant powinien narysowania natychmiast po ustawienia czcionki. Ustawienie tego parametru **TRUE** powoduje, że formant ponownego narysowania.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [DTM_SETMCFONT](http://msdn.microsoft.com/library/windows/desktop/bb761775), zgodnie z opisem w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#7](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]  
  
> [!NOTE]
>  Jeśli używasz tego kodu, należy być członkiem sieci `CDialog`-klasy o nazwie `m_MonthFont` typu **cfont —**.  
  
##  <a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle  
 Ustawia styl formant kalendarza miesięcznego listy rozwijanej, która jest skojarzona z bieżącym formant wyboru daty i godziny.  
  
```  
DWORD SetMonthCalStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|[in]`dwStyle`|Styl formantu kalendarza nowy miesiąc, czyli bitowe połączenie stylów formantu kalendarza miesięcznego (lub). Aby uzyskać więcej informacji, zobacz [stylów formantu kalendarza miesięcznego](http://msdn.microsoft.com/library/windows/desktop/bb760919).|  
  
### <a name="return-value"></a>Wartość zwracana  
 Styl poprzedniej formant kalendarza miesięcznego listy rozwijanej.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wysyła [DTM_SETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761778) komunikat, który jest opisany w zestawie SDK systemu Windows.  
  
### <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje zmienną, `m_dateTimeCtrl`, która jest używana do uzyskania programowego dostępu do formant wyboru daty i godziny. Ta zmienna jest używana w następnym przykładzie.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Przykład  
 Poniższy przykład kodu Określa formant wyboru daty i godziny, aby wyświetlać numery tygodni, skróconej nazwy dni tygodnia, a nie wskaźnik dziś.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]  
  
##  <a name="setrange"></a>CDateTimeCtrl::SetRange  
 Ustawia czas minimalne i maksymalne dozwolone systemu dla formant wyboru daty i godziny.  
  
```  
BOOL SetRange(
    const COleDateTime* pMinRange,  
    const COleDateTime* pMaxRange);

 
BOOL SetRange(
    const CTime* pMinRange,  
    const CTime* pMaxRange);
```  
  
### <a name="parameters"></a>Parametry  
 `pMinRange`  
 Wskaźnik do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiektu lub [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiekt zawierający najwcześniejszym terminie w `CDateTimeCtrl` obiektu.  
  
 `pMaxRange`  
 Wskaźnik do `COleDateTime` obiektu lub `CTime` obiekt zawierający Najpóźniejsza godzina dozwolone w `CDateTimeCtrl` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [DTM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761780), zgodnie z opisem w zestawie Windows SDK. W implementacji MFC, można określić albo `COleDateTime` lub `CTime` użycia. Jeśli `COleDateTime` obiekt ma **NULL** stan, zakres zostaną usunięte. Jeśli `CTime` wskaźnika lub `COleDateTime` wskaźnika jest **NULL**, zakres zostaną usunięte.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CDateTimeCtrl::GetRange](#getrange).  
  
##  <a name="settime"></a>CDateTimeCtrl::SetTime  
 Ustawia czas w formancie selektora daty i godziny.  
  
```  
BOOL SetTime(const COleDateTime& timeNew);  
BOOL SetTime(const CTime* pTimeNew);  
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *timeNew*  
 Odwołanie do [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) obiekt zawierający do której zostanie ustawiona formantu.  
  
 *pTimeNew*  
 W drugiej wersji powyżej wskaźnik do [ctime —](../../atl-mfc-shared/reference/ctime-class.md) obiekt zawierający godzinę, do której zostanie ustawiona formantu. W trzeciej wersji powyżej wskaźnik do [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktury zawierającej czasu, do którego zostanie ustawiona formantu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska implementuje zachowanie komunikatu Win32 [DTM_SETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761782), zgodnie z opisem w zestawie Windows SDK. W implementacji MFC **SetTime**, można użyć `COleDateTime` lub `CTime` klas, lub użyć `SYSTEMTIME` struktury, aby ustawić informacje o godzinie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_CDateTimeCtrl#8](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [CMNCTRL1 próbki MFC](../../visual-cpp-samples.md)   
 [Klasa CWnd](../../mfc/reference/cwnd-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cmonthcalctrl — klasa](../../mfc/reference/cmonthcalctrl-class.md)
