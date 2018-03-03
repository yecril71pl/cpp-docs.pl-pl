---
title: Klasa CDebugReportHook | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: df098ee80bcd8fa81b5503cc21b08ded86945a72
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdebugreporthook-class"></a>Klasa CDebugReportHook
Klasa używana do wysyłania raportów debugowania do nazwanego potoku.  
  
## <a name="syntax"></a>Składnia  
  
```
class CDebugReportHook
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Wywołania [SetPipeName](#setpipename), [SetTimeout](#settimeout), i [SetHook](#sethook).|  
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|Wywołania [CDebugReportHook::RemoveHook](#removehook).|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Statyczny) Funkcję raportowania niestandardową, który jest punktem zaczepienia C-run-time debugowania procesu raportowania.|  
|[CDebugReportHook::RemoveHook](#removehook)|Wywołanie tej metody, aby zatrzymać wysyłanie raportów debugowania do nazwanego potoku i przywrócenie poprzedniego punktu zaczepienia raportu.|  
|[CDebugReportHook::SetHook](#sethook)|Wywołaj tę metodę, aby rozpocząć wysyłanie raportów debugowania do nazwanego potoku.|  
|[CDebugReportHook::SetPipeName](#setpipename)|Wywołaj tę metodę, aby ustawić komputera i nazwy potoku, do którego będą wysyłane raporty debugowania.|  
|[CDebugReportHook::SetTimeout](#settimeout)|Wywołanie tej metody, aby ustawić czas (w milisekundach), czy ta klasa będzie oczekiwał na udostępnienie nazwanego potoku.|  
  
## <a name="remarks"></a>Uwagi  
 Utwórz wystąpienie tej klasy w kompilacjach debugowania usług lub aplikacji na wysyłanie raportów debugowania do nazwanego potoku. Debugowania raporty są generowane przez wywołanie metody [_crtdbgreport —](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) lub użyć otokę dla tej funkcji, takich jak [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) i [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) makra.  
  
 Użyj tej klasy umożliwia interakcyjne debugowania składniki działające w nieinterakcyjnym [stacji okna](http://msdn.microsoft.com/library/windows/desktop/ms687096).  
  
 Należy pamiętać, że debugowania raporty są wysyłane przy użyciu kontekstu zabezpieczeń źródłowego wątku. Personifikacja jest tymczasowo wyłączona, aby wyświetlić raporty debugowania w sytuacjach, w którym niskim poziomem uprawnień użytkowników jest personifikacja, takich jak w aplikacji sieci web.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlutil.h  
  
##  <a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook  
 Wywołania [SetPipeName](#setpipename), [SetTimeout](#settimeout), i [SetHook](#sethook).  
  
```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `szMachineName`  
 Nazwa komputera, do którego mają być wysyłane dane wyjściowe debugowania. Wartość domyślna to komputer lokalny.  
  
 `szPipeName`  
 Nazwa nazwany potok, do którego mają być wysyłane dane wyjściowe debugowania.  
  
 `dwTimeout`  
 Czas (w milisekundach), czy ta klasa będzie oczekiwał na udostępnienie nazwanego potoku.  
  
##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook  
 Wywołania [CDebugReportHook::RemoveHook](#removehook).  
  
```
~CDebugReportHook() throw();
```  
  
##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc  
 Funkcję raportowania niestandardową, który jest punktem zaczepienia C-run-time debugowania procesu raportowania.  
  
```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `reportType`  
 Typ raportu (_CRT_WARN, _CRT_ERROR lub _CRT_ASSERT).  
  
 `message`  
 Ciąg komunikatu.  
  
 *returnValue*  
 Wartość, która ma zostać zwrócony przez [_crtdbgreport —](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość FALSE, jeśli haku obsługi wiadomości w całkowicie tak, aby nie dalsze raportowania jest wymagana. Zwraca wartość PRAWDA, jeśli `_CrtDbgReport` Zgłoś komunikatu w normalny sposób.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja raportowania próbuje otworzyć nazwanego potoku i komunikacji z procesem na drugim końcu. Jeśli potoku są zajęte, funkcja raportowania czeka na zakończenie potoku jest bezpłatna lub upłynięciem limitu czasu. Można ustawić limitu czasu przez konstruktora lub wywołanie [CDebugReportHook::SetTimeout](#settimeout).  
  
 Kod w tej funkcji jest wykonywany w kontekście zabezpieczeń podstawowym wątku, czyli personifikacji jest wyłączone na czas trwania tej funkcji.  
  
##  <a name="removehook"></a>CDebugReportHook::RemoveHook  
 Wywołanie tej metody, aby zatrzymać wysyłanie raportów debugowania do nazwanego potoku i przywrócenie poprzedniego punktu zaczepienia raportu.  
  
```
void RemoveHook() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [_crtsetreporthook2 —](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) do przywrócenia poprzedniego punktu zaczepienia raportu.  
  
##  <a name="sethook"></a>CDebugReportHook::SetHook  
 Wywołaj tę metodę, aby rozpocząć wysyłanie raportów debugowania do nazwanego potoku.  
  
```
void SetHook() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [_crtsetreporthook2 —](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) do debugowania raportów kierowany przez [CDebugReportHookProc](#cdebugreporthookproc) do nazwanego potoku. Ta klasa przechowuje informacje o poprzednich punktów zaczepienia raportu tak, aby można go przywrócić kiedy [RemoveHook](#removehook) jest wywoływana.  
  
##  <a name="setpipename"></a>CDebugReportHook::SetPipeName  
 Wywołaj tę metodę, aby ustawić komputera i nazwy potoku, do którego będą wysyłane raporty debugowania.  
  
```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```  
  
### <a name="parameters"></a>Parametry  
 `szMachineName`  
 Nazwa komputera, do którego mają być wysyłane dane wyjściowe debugowania.  
  
 `szPipeName`  
 Nazwa nazwany potok, do którego mają być wysyłane dane wyjściowe debugowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA w przypadku powodzenia FALSE w przypadku awarii.  
  
##  <a name="settimeout"></a>CDebugReportHook::SetTimeout  
 Wywołanie tej metody, aby ustawić czas (w milisekundach), czy ta klasa będzie oczekiwał na udostępnienie nazwanego potoku.  
  
```
void SetTimeout(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>Parametry  
 `dwTimeout`  
 Czas (w milisekundach), czy ta klasa będzie oczekiwał na udostępnienie nazwanego potoku.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../atl/reference/atl-classes.md)
