---
title: Debugowanie i funkcje globalne raportów o błędach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
dev_langs:
- C++
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d41cc60b9a30254e46a9ca3ef3d3ad7dbc0dfcfb
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882916"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Debugowanie i funkcje globalne raportowanie błędów
Te funkcje zapewniają przydatny urządzenia debugowania i śledzenia.  
  
|||  
|-|-|  
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Zwraca `GetLastError` kod błędu w formie HRESULT.|  
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Konwertuje kod błędu Win32 na HRESULT.|  
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Konfiguruje `IErrorInfo` zapewnienie szczegóły błędu do klienta.|  
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Zgłasza `CAtlException`.|  
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Wywołaj tę funkcję, aby zasygnalizować błąd na podstawie wyniku funkcji Windows `GetLastError`.|  
  
##  <a name="atlhresultfromlasterror"></a>  AtlHresultFromLastError  
 Zwraca wartość kodu ostatniego błędu wywołującego wątku w formie HRESULT.  
  
```
HRESULT AtlHresultFromLastError();
```  
  
### <a name="remarks"></a>Uwagi  
 `AtlHresultFromLastError` wywołania `GetLastError` uzyskać ostatnim błędem i zwraca błąd podczas konwertowania go na błąd HRESULT, użycie makra HRESULT_FROM_WIN32.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcomcli.h  

##  <a name="atlhresultfromwin32"></a>  AtlHresultFromWin32  
 Konwertuje kod błędu Win32 na HRESULT.  
  
```
AtlHresultFromWin32(DWORD error);
```  
  
### <a name="parameters"></a>Parametry  
 *Błąd*  
 Wartość błędu do przekonwertowania.  
  
### <a name="remarks"></a>Uwagi  
 Konwertuje kod błędu Win32 na HRESULT, użycie makra HRESULT_FROM_WIN32.  
  
> [!NOTE]
>  Zamiast używania `HRESULT_FROM_WIN32(GetLastError())`, należy użyć funkcji [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcomcli.h  

##  <a name="atlreporterror"></a>  AtlReportError  
 Konfiguruje `IErrorInfo` interfejs w celu dostarczenia informacji o błędach do klientów obiektu.  
  
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
 *Identyfikator klasy*  
 [in] Identyfikator CLSID obiektu zgłoszenie błędu.  
  
 *lpszDesc*  
 [in] Ciąg opisujący błąd. Wersje Unicode określić, że *lpszDesc* jest typ LPCOLESTR; wersji ANSI Określa typ LPCSTR.  
  
 *IID*  
 [in] Identyfikator IID interfejsu Definiowanie błąd lub GUID_NULL, jeśli ten błąd jest zdefiniowany przez system operacyjny.  
  
 *parametrem typu HRESULT*  
 [in] Wartość HRESULT, które mają zwracany do obiektu wywołującego.  
  
 *nID*  
 [in] Identyfikator zasobu, gdzie znajduje się ciąg opisu błędu. Ta wartość musi zawierać się między 0x0200 i 0xFFFF, włącznie. W kompilacjach do debugowania **ASERCJA** spowoduje, że jeśli *nID* indeksowania prawidłowy ciąg. W kompilacjach do wydania ciąg opisu błędu zostanie ustawiony na "Nieznany błąd."  
  
 *dwHelpID*  
 [in] Identyfikator kontekstu pomocy dla błędu.  
  
 *lpszHelpFile*  
 [in] Ścieżka i nazwa pliku pomocy, opisujący błąd.  
  
 *hInst*  
 [in] Dojście do zasobu. Domyślnie ten parametr jest `__AtlBaseModuleModule::GetResourceInstance`, gdzie `__AtlBaseModuleModule` jest globalne wystąpienie [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) lub klasa pochodnej od niego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli *parametrem typu HRESULT* parametr jest różna od zera, zwraca wartość *parametrem typu HRESULT*. Jeśli *parametrem typu HRESULT* jest zero, a następnie pierwsze cztery wersje `AtlReportError` zwraca DISP_E_EXCEPTION. Ostatnie dwie wersje zwracają wynik makra **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.  
  
### <a name="remarks"></a>Uwagi  
 Ciąg *lpszDesc* służy jako opis błędu. Gdy klient odbierze *parametrem typu HRESULT* zwracanie z `AtlReportError`, ten klient uzyskuje dostęp `IErrorInfo` struktury, aby uzyskać szczegółowe informacje o błędzie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]  
  
> [!CAUTION]
>  Nie używaj `AtlReportError` catch — Obsługa w języku C++. Zastąpienia, niektóre z tych funkcji korzystanie z makr konwersji ciągu ATL, który z kolei użyj `_alloca` funkcji wewnętrznie. Za pomocą `AtlReportError` w bloku catch języka C++ program obsługi może spowodować wyjątki obsługi catch języka C++.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcom.h  
    
##  <a name="atlthrow"></a>  AtlThrow  
 Wywołaj tę funkcję, aby zasygnalizować błąd na podstawie kodu stanu HRESULT.  
  
```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```  
  
### <a name="parameters"></a>Parametry  
 *godz.*  
 Standardowe wartości HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana przez kodu ATL i MFC w przypadku wystąpienia błędu. Mogą być również wywoływane z własnego kodu. Domyślna implementacja tej funkcji zależy od definicji _ATL_NO_EXCEPTIONS symboli i typ projektu, MFC ani ATL.  
  
 We wszystkich przypadkach ta funkcja służy do śledzenia HRESULT do debugera.  
  
 W programie Visual Studio 2015 Update 3 i nowszych ta funkcja jest opartego na atrybutach __declspec(noreturn) w celu uniknięcia ostrzeżeń SAL fałszywe.  
  
 Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowana w projekcie MFC, ta funkcja zgłosi [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md) na podstawie wartości HRESULT.  
  
 Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowana w projekcie ATL, funkcja zgłasza [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Jeśli nie zdefiniowano _ATL_NO_EXCEPTIONS, funkcja powoduje błąd potwierdzenia zamiast zgłaszać wyjątek.  
  
 W przypadku projektów ATL jest możliwe podanie własnej implementacji tej funkcji, który będzie używany przez ATL awarii. Aby to zrobić, należy zdefiniować funkcję z taką samą sygnaturę jak `AtlThrow` i #define `AtlThrow` nazwę funkcji. Należy to zrobić przed dołączeniem atlexcept.h (co oznacza, że musi zostać wykonana przed tym wszelkie nagłówki ATL, ponieważ atlbase.h zawiera atlexcept.h). Atrybut funkcji `__declspec(noreturn)` w celu uniknięcia ostrzeżeń SAL fałszywe.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldef.h  

##  <a name="atlthrowlastwin32"></a>  AtlThrowLastWin32  
 Wywołaj tę funkcję, aby zasygnalizować błąd na podstawie wyniku funkcji Windows `GetLastError`.  
  
```
inline void AtlThrowLastWin32();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja służy do śledzenia wynik `GetLastError` do debugera.  
  
 Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowana w projekcie MFC, ta funkcja zgłosi [CMemoryException](../../mfc/reference/cmemoryexception-class.md) lub [COleException](../../mfc/reference/coleexception-class.md) na podstawie wartości zwracane przez `GetLastError`.  
  
 Jeśli _ATL_NO_EXCEPTIONS nie jest zdefiniowana w projekcie ATL, funkcja zgłasza [CAtlException](../../atl/reference/catlexception-class.md).  
  
 Jeśli nie zdefiniowano _ATL_NO_EXCEPTIONS, funkcja powoduje błąd potwierdzenia zamiast zgłaszać wyjątek.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldef.h  
   
     
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../atl/reference/atl-functions.md)   
 [Makra debugowania i raportowania błędów](../../atl/reference/debugging-and-error-reporting-macros.md)









