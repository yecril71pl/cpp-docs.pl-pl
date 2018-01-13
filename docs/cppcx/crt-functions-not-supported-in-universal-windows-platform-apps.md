---
title: "Funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 65d058780ee71731559733ac07eef3f614a47784
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>Funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows
Wiele C runtime (CRT) są niedostępne podczas tworzenia aplikacji uniwersalnych platformy systemu Windows (UWP). W niektórych przypadkach są dostępne rozwiązania — — na przykład można użyć środowiska wykonawczego systemu Windows lub interfejsów API systemu Win32. Jednak w innych przypadkach funkcje CRT mają zakazany ponieważ funkcje, które odpowiadają je lub interfejsów API obsługi nie są stosowane w aplikacjach platformy uniwersalnej systemu Windows.  
  
 Poniższa tabela zawiera listę funkcji CRT, które nie są dostępne podczas tworzenia aplikacji platformy uniwersalnej systemu Windows oraz wskazuje wszystkie rozwiązania, które są stosowane.  
  
## <a name="unsupported-crt-functions"></a>Funkcje nieobsługiwane CRT  
  
||||  
|-|-|-|  
|_beep _sleep _seterrormode|Tych funkcji były przestarzałe w poprzednich wersjach CRT. Ponadto odpowiednich interfejsów API Win32 nie są dostępne dla aplikacji platformy uniwersalnej systemu Windows.|Brak obejścia.|  
|getcwd — _chdrive — chdir|Te funkcje są przestarzałe lub nie są wątkowo.|_Chdir — Użyj _getcwd — i powiązane funkcje.|  
|_cgets — _cgets_s — _cgetws — _cgetws_s — _cprintf — _cprintf_l — _cprintf_p — _cprintf_p_l — _cprintf_s — _cprintf_s_l — _cputs — _cputws — _cscanf — _cscanf_l — _cscanf_s — _cscanf_s_l — _cwait — _cwprintf — _cwprintf_l — _cwprintf_p — _cwprintf_p_l — _cwprintf_s — _cwprintf_s_l — _cwscanf — _ cwscanf_l — _cwscanf_s — _cwscanf_s_l — _vcprintf — _vcprintf_l — _vcprintf_p — _vcprintf_p_l — _vcprintf_s — _vcprintf_s_l — _vcwprintf — _vcwprintf_l — _vcwprintf_p — _vcwprintf_p_l — _vcwprintf_s — _vcwprintf_s_l — _getch — _getch_nolock — _getche — _getche_nolock — _getwch — _ getwch_nolock — _getwche — _getwche_nolock — _putch — _putch_nolock — _putwch — _putwch_nolock — _ungetch — _ungetch_nolock — _ungetwch — _ungetwch_nolock — _kbhit — kbhit — putch — cgets — cprintf — cputs — cscanf — cwait — getch — getche — ungetch —|Funkcje te służą do odczytu i zapisu bezpośrednio z i do konsoli. Aplikacje platformy uniwersalnej systemu Windows są graficznego interfejsu użytkownika. nie obsługują konsoli.|Brak obejścia.|  
|getpid|Ta funkcja jest przestarzała.|Użyj _getpid — lub interfejsu API Win32 `GetCurrentProcessId()`.|  
|_getdiskfree|Nie jest dostępna.|Za pomocą interfejsu API Win32 `GetDiskFreeSpaceExW()`.|  
|_getdrives — _getdrive —|Odpowiedni interfejs API nie jest dostępna dla aplikacji platformy uniwersalnej systemu Windows.|Brak obejścia.|  
|_inp — _inpd — _inpw — _outp — _outpd — _outpw — inp inpd — inpw — Dz outpd — outpw —|Portów We/Wy nie jest obsługiwane w aplikacjach platformy uniwersalnej systemu Windows.|Brak obejścia.|  
|_ismbcalnum — _ismbcalnum_l — _ismbcalpha — _ismbcalpha_l — _ismbcdigit — _ismbcdigit_l — _ismbcgraph — _ismbcgraph_l — _ismbchira — _ismbchira_l — _ismbckata — _ismbckata_l — _ismbcl0 — _ismbcl0_l — _ismbcl1 — _ismbcl1_l — _ismbcl2 — _ismbcl2_l — _ismbclegal — _ismbclegal_l — _ ismbclower — _ismbclower_l — _ismbcprint — _ismbcprint_l — _ismbcpunct — _ismbcpunct_l — _ismbcspace — _ismbcspace_l — _ismbcsymbol — _ismbcsymbol_l — _ismbcupper — _ismbcupper_l — _mbbtombc — _mbbtombc_l — _mbbtype — _mbbtype_l — _mbccpy — _mbccpy_l — _mbccpy_s — _mbccpy_s_l — _ mbcjistojms — _mbcjistojms_l — _mbcjmstojis — _mbcjmstojis_l — _mbclen — _mbclen_l _mbctohira — _mbctohira_l — _mbctokata — _mbctokata_l — _mbctolower — _mbctolower_l — _mbctombb — _mbctombb_l — _mbctoupper — _mbctoupper_l — _mbsbtype — _mbsbtype_l — _mbscat — _mbscat_l _mbscat_s — _ mbscat_s_l _mbschr — _mbschr_l — _mbscmp — _mbscmp_l _mbscoll — _mbscoll_l _mbscpy — _mbscpy_l _mbscpy_s — _mbscpy_s_l _mbscspn — _mbscspn_l — _mbsdec _mbsdec_l _mbsicmp — _mbsicmp_l — _mbsicoll — _mbsicoll_l — _mbsinc _mbsinc_l _mbslen — _mbslen_l — _mbslwr — _mbslwr_l — _mbslwr_s — _mbslwr_s_l — _mbsnbcat — _mbsnbcat_l — _mbsnbcat_s — _mbsnbcat_s_l — _mbsnbcmp — _mbsnbcmp_l — _mbsnbcnt _mbsnbcnt_l _mbsnbcoll — _mbsnbcoll_l — _mbsnbcpy — _mbsnbcpy_l — _mbsnbcpy_s — _mbsnbcpy_s_l — _mbsnbicmp — _mbsnbicmp_l — _mbsnbicoll — _mbsnbicoll_l — _mbsnbset — _mbsnbset — _l _mbsnbset_s — _mbsnbset_s_l — _mbsncat — _mbsncat_l — _mbsncat_s — _mbsncat_s_l — _mbsnccnt _mbsnccnt_l _mbsncmp — _mbsncmp_l — _mbsncoll — _mbsncoll_l — _mbsncpy — _mbsncpy_l — _mbsncpy_s _mbsncpy_s_l _mbsnextc _mbsnextc_l _mbsnicmp — _mbsnicmp_l — _mbsnicoll — _mbsnicoll_ l _mbsninc _mbsninc_l _mbsnlen — _mbsnlen_l — _mbsnset — _mbsnset_l — _mbsnset_s — _mbsnset_s_l — _mbspbrk — _mbspbrk_l — _mbsrchr — _mbsrchr_l — _mbsrev — _mbsrev_l — _mbsset — _mbsset_l — _mbsset_s — _mbsset_s_l — _mbsspn — _mbsspn_l — _mbsspnp _mbsspnp_l _mbsstr — _mbsstr_l — _mbstok — _ mbstok_l — _mbstok_s — _mbstok_s_l — _mbsupr — _mbsupr_l — _mbsupr_s — _mbsupr_s_l — is_wctype|Ciągi wielobajtowe nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows.|Zamiast tego użyj ciągów Unicode.|  
|_wpopen — _popen — _pipe — _pclose —|Funkcja potoku nie jest dostępne dla aplikacji platformy uniwersalnej systemu Windows.|Brak obejścia.|  
|_resetstkoflw|Pomocnicze API Win32 nie są dostępne dla aplikacji platformy uniwersalnej systemu Windows.|Brak obejścia.|  
|_getsystime _setsystime|Były przestarzałe interfejsy API w poprzednich wersjach CRT. Ponadto użytkownik nie można ustawić czasu systemowego w aplikacji platformy uniwersalnej systemu Windows, które powinny przejść z braku uprawnień.|Aby uzyskać ustawienia zegara systemowego, należy użyć interfejsu API Win32 `GetSystemTime`. Nie można ustawić czasu systemowego.|  
|_environ — _putenv — _putenv_s — _searchenv — _searchenv_s — _dupenv_s — _wputenv — _wputenv_s — _wsearchenv — getenv — getenv_s — putenv — _wdupenv_s — _wenviron — _wgetenv — _wgetenv_s — _wsearchenv_s — tzset —|Zmienne środowiskowe nie są dostępne do aplikacji platformy uniwersalnej systemu Windows.|Brak obejścia. Aby ustawić strefy czasowej, użyj _tzset —.|  
|_loaddll _getdllprocaddr _unloaddll|Były przestarzałe funkcje we wcześniejszych wersjach CRT. Ponadto użytkownika nie można załadować biblioteki dll, z wyjątkiem od tych w tym samym pakiecie aplikacji.|Przy użyciu interfejsów API Win32 `LoadPackagedLibrary`, `GetProcAddress`, i `FreeLibrary` do ładowania i używać spakowanych bibliotek DLL.|  
|_wexecl — _wexecle — _wexeclp — _wexeclpe — _wexecv — _wexecve — _wexecvp — _wexecvpe — _execl — _execle — _execlp — _execlpe — _execv — _execve — _execvp — _execvpe — _spawnl — _spawnle — _spawnlp — _spawnlpe — _spawnv — _spawnve — _spawnvp — _spawnvpe — _wspawnl — _wspawnle — _wspawnlp — _wspawnlpe — _ wspawnv — _wspawnve — _wspawnvp — _wspawnvpe — _wsystem — execl — execle — execlp — execlpe — execv — execve — execvp — execvpe — spawnl — spawnle — spawnlp — spawnlpe — spawnv — spawnve — spawnvp — spawnvpe — systemu|Funkcja nie jest dostępna w aplikacjach platformy uniwersalnej systemu Windows. Aplikacji platformy uniwersalnej systemu Windows nie można wywołać w innej aplikacji platformy uniwersalnej systemu Windows lub aplikacji komputerowej.|Brak obejścia.|  
|_heapwalk — _heapadd — _heapchk — _heapset — _heapused|Funkcje te są zwykle używane do pracy ze stosem. Odpowiednie API Win32 nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows. I aplikacji nie można utworzyć lub użyć stosów prywatnych.|Brak obejścia. Jednak `_heapwalk` dostępne w debugowania CRT, tylko do celów debugowania. Nie może być one używane w aplikacjach, które są przekazywane do Sklepu Windows.|  
  
 Następujące funkcje są dostępne w CRT dla aplikacji platformy uniwersalnej systemu Windows, ale należy używać tylko wtedy, gdy nie można użyć odpowiednich Win32 lub interfejsów API środowiska wykonawczego systemu Windows — na przykład podczas przenoszenia dużych baz kodu  
  
|||  
|-|-|  
|Funkcje ciągów jednobajtowe — na przykład `strcat`, `strcpy`, `strlwr`i tak dalej.|Aplikacji platformy uniwersalnej systemu Windows należy ściśle Unicode ponieważ jest używany przez wszystkie interfejsy API Win32 i interfejsów API środowiska wykonawczego systemu Windows, które są widoczne tylko zestawy znaków Unicode.  Funkcje jednobajtowe pozostawiono dla eksportowanie dużej kodu podstawowych, ale w przeciwnym razie należy unikać i odpowiednie funkcje znaków powinna być używana zamiast tego, jeśli to możliwe.|  
|Strumień we/wy i funkcje We/Wy niskiego poziomu pliku — na przykład `fopen`, `open`i tak dalej.|Te funkcje są synchroniczne, który nie jest zalecane dla aplikacji platformy uniwersalnej systemu Windows. W aplikacji platformy uniwersalnej systemu Windows otwórz, Odczytaj z przy użyciu interfejsów API asynchroniczne i zapisywanie do plików, aby zapobiec blokowaniu wątku interfejsu użytkownika. Przykłady takich interfejsy API są pokazane w `Windows::Storage::FileIO` klasy.|  
  
## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Aplikacje ze Sklepu Windows 8.x i Windows Phone 8.x aplikacji  
 Oprócz wspomnianych interfejsów API następujące interfejsy API nie są dostępne w aplikacji ze Sklepu Windows 8.x i Windows Phone 8.x aplikacji.  
  
||||  
|-|-|-|  
|_endthreadex — _endthread — _beginthreadex — _beginthread —|Wątkowości API Win32 nie są dostępne w aplikacji ze Sklepu Windows 8.x.|Użyj `Windows Runtime Windows::System::Threading::ThreadPool` lub `concurrency::task` zamiast tego.|  
|_wgetdcwd — _chdir — _wchdir — _getcwd — _getdcwd — _wgetcwd —|Pojęcie katalog roboczy nie odnoszą się do aplikacji ze Sklepu Windows 8.x.|Zamiast tego użyj pełnej ścieżki.|  
|_getpid|Ta funkcja były przestarzałe w poprzednich wersjach CRT.|Za pomocą interfejsu API Win32`GetCurrentProcessId()`|  
|_ismbbalnum — _isleadbyte_l —, _ismbbalnum_l —, _ismbbalpha — _ismbbalpha — _ismbbalpha_l — _ismbbgraph — _ismbbgraph_l — _ismbbkalnum — _ismbbkalnum_l — _ismbbkana — _ismbbkana_l — _ismbbkprint — _ismbbkprint_l — _ismbbkpunct — _ismbbkpunct_l — _ismbblead — _ismbblead_l — _ ismbbprint — _ismbbprint_l — _ismbbpunct — _ismbbpunct_l — _ismbbtrail — _ismbbtrail_l — _ismbslead — _ismbslead_l — _ismbstrail — _ismbstrail_l — _mbsdup — isleadbyte —|Ciągi wielobajtowe nie są obsługiwane w aplikacji ze Sklepu Windows 8.x.|Zamiast tego użyj ciągów Unicode.|  
|_tzset|Zmienne środowiskowe nie są dostępne dla aplikacji ze Sklepu Windows 8.x.|Brak obejścia.|  
|_get_heap_handle —, _heapmin —|Odpowiednich interfejsów API Win32 nie są obsługiwane w aplikacji ze Sklepu Windows 8.x. I aplikacje nie mogą już tworzyć stosów prywatnych.|Brak obejścia. Jednak `_get_heap_handle` jest dostępna w debugowania CRT, tylko do celów debugowania.|