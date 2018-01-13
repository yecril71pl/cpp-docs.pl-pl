---
title: "Debugowanie i funkcje globalne raportowania błędów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
dev_langs: C++
helpviewer_keywords: functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b3383efcc78a022fc5131984957d94aa4b47838
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-error-reporting-global-functions"></a>Debugowanie i funkcje globalne raportowania błędów
Te funkcje udostępniać przydatne narzędzia debugowania i śledzenia.  
  
|||  
|-|-|  
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Zwraca `GetLastError` kod błędu w formie typu danych HRESULT.|  
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Konwertuje kod błędu Win32 na HRESULT.|  
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Konfiguruje **IErrorInfo** zapewniające informacje o błędzie do klienta.|  
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Zgłasza wyjątek `CAtlException`.|  
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Wywołanie tej funkcji w celu zasygnalizowania błędu na podstawie wyniku funkcji systemu Windows `GetLastError`.|  
  
##  <a name="atlhresultfromlasterror"></a>AtlHresultFromLastError  
 Zwraca wartość kodu ostatniego błędu wywołującego wątku w formie HRESULT.  
  
```
HRESULT AtlHresultFromLastError();
```  
  
### <a name="remarks"></a>Uwagi  
 `AtlHresultFromLastError`wywołania `GetLastError` można uzyskać z ostatnim błędem i zwraca błąd po przekonwertowaniu go do HRESULT za pomocą **HRESULT_FROM_WIN32** makra.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcomcli.h  

##  <a name="atlhresultfromwin32"></a>AtlHresultFromWin32  
 Konwertuje kod błędu Win32 na HRESULT.  
  
```
AtlHresultFromWin32(DWORD error);
```  
  
### <a name="parameters"></a>Parametry  
 *Błąd*  
 Błąd wartość do przekonwertowania.  
  
### <a name="remarks"></a>Uwagi  
 Konwertuje kod błędu Win32 HRESULT, za pomocą makra **HRESULT_FROM_WIN32**.  
  
> [!NOTE]
>  Zamiast **HRESULT_FROM_WIN32(GetLastError())**, należy użyć funkcji [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcomcli.h  

##  <a name="atlreporterror"></a>AtlReportError  
 Konfiguruje `IErrorInfo` interfejsu, aby zapewnić klientom obiektu informacji o błędzie.  
  
```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 [in] Identyfikator CLSID obiektu zgłoszenie błędu.  
  
 `lpszDesc`  
 [in] Ciąg opisujący błąd. Wersje Unicode określić, że `lpszDesc` jest typu **LPCOLESTR**; wersji ANSI Określa typ `LPCSTR`.  
  
 `iid`  
 [in] Uzyskanie identyfikatora IID interfejsu Definiowanie błąd lub `GUID_NULL` Jeśli błąd został zdefiniowany przez system operacyjny.  
  
 `hRes`  
 [in] `HRESULT` Ma zwracany do obiektu wywołującego.  
  
 `nID`  
 [in] Identyfikator zasobu przechowywania ciąg opisu błędu. Ta wartość musi zawierać się między 0x0200 i 0xFFFF, włącznie. W kompilacjach do debugowania **ASSERT** spowoduje `nID` nie indeksowania prawidłowy ciąg. W kompilacjach wydania ciąg opisu błędu zostanie ustawiona na "Unknown Error".  
  
 `dwHelpID`  
 [in] Identyfikator kontekstu pomocy dla błędu.  
  
 `lpszHelpFile`  
 [in] Ścieżka i nazwa pliku pomocy opisem błędu.  
  
 `hInst`  
 [in] Dojście do zasobu. Domyślnie ten parametr jest **__AtlBaseModuleModule::GetResourceInstance**, gdzie **__AtlBaseModuleModule** jest globalne wystąpienie [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) lub klasy pochodzić od niego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli `hRes` parametru jest różna od zera, zwraca wartość `hRes`. Jeśli `hRes` jest zero, a następnie pierwsze cztery wersje `AtlReportError` zwracać `DISP_E_EXCEPTION`. Ostatnie dwie wersje zwracają wynik makra **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.  
  
### <a name="remarks"></a>Uwagi  
 Ciąg *lpszDesc* służy jako opis błędu. Gdy klient odbierze `hRes` zwróconych z `AtlReportError`, ten klient uzyskuje dostęp **IErrorInfo** struktury, aby uzyskać szczegółowe informacje o błędzie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]  
  
> [!CAUTION]
>  Nie używaj `AtlReportError` catch — Obsługa w języku C++. Zastąpienia niektóre z tych funkcji korzystanie z makra konwersji ciągu ATL, który z kolei użyj `_alloca` funkcji wewnętrznie. Przy użyciu `AtlReportError` w instrukcji catch C++ obsługi może spowodować wyjątków w języku C++ obsługi catch.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
    
##  <a name="atlthrow"></a>AtlThrow  
 Wywołanie tej funkcji w celu zasygnalizowania błędu na podstawie `HRESULT` kod stanu.  
  
```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```  
  
### <a name="parameters"></a>Parametry  
 `hr`  
 Standardowa wartość HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana przez kodu ATL i MFC w przypadku warunek błędu. Można również nadać mu z własnego kodu. Domyślna implementacja tej funkcji zależy od definicji symbolu **_ATL_NO_EXCEPTIONS** i typu projektu, MFC lub ATL.  
  
 We wszystkich przypadkach ta funkcja służy do śledzenia HRESULT do debugera.  
  
 W programie Visual Studio 2015 Update 3 i nowszych ta funkcja jest oparte na atrybutach __declspec(noreturn), aby uniknąć fałszywe ostrzeżeń SAL.  
  
 Jeśli **_ATL_NO_EXCEPTIONS** nie jest zdefiniowany w projekcie MFC, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md) na podstawie wartości HRESULT.  
  
 Jeśli **_ATL_NO_EXCEPTIONS** nie jest zdefiniowany w Projekt ATL, funkcja zwraca [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Jeśli **_ATL_NO_EXCEPTIONS** jest zdefiniowany, funkcja powoduje błąd potwierdzenia zamiast generowania wyjątku.  
  
 W przypadku projektów ATL jest możliwe zapewnienie implementacji tej funkcji, które mają być używane przez ATL w przypadku awarii. Aby to zrobić, należy zdefiniować funkcji z takiego samego podpisu jak `AtlThrow` i #define `AtlThrow` nazwę funkcji. Należy to zrobić przed dołączeniem atlexcept.h (co oznacza, że musi zostać wykonana przed tym wszelkie nagłówki ATL, ponieważ atlbase.h obejmuje atlexcept.h). Atrybut funkcji `__declspec(noreturn)` w celu uniknięcia fałszywe ostrzeżeń SAL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldef.h  

##  <a name="atlthrowlastwin32"></a>AtlThrowLastWin32  
 Wywołanie tej funkcji w celu zasygnalizowania błędu na podstawie wyniku funkcji systemu Windows `GetLastError`.  
  
```
inline void AtlThrowLastWin32();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do śledzenia wynik `GetLastError` do debugera.  
  
 Jeśli **_ATL_NO_EXCEPTIONS** nie jest zdefiniowany w projekcie MFC, funkcja zwraca [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md) na podstawie wartości zwracanych przez `GetLastError`.  
  
 Jeśli **_ATL_NO_EXCEPTIONS** nie jest zdefiniowany w Projekt ATL, funkcja zwraca [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Jeśli **_ATL_NO_EXCEPTIONS** jest zdefiniowany, funkcja powoduje błąd potwierdzenia zamiast generowania wyjątku.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldef.h  
   
     
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)   
 [Makra debugowania i raportowania błędów](../../atl/reference/debugging-and-error-reporting-macros.md)









