---
title: Funkcje CRT nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows
ms.date: 12/30/2016
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
ms.openlocfilehash: cf67cb9c0a2438ee6ac1bcc7753c0f89b63a356d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214321"
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>Funkcje CRT nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows

Wiele funkcji środowiska uruchomieniowego języka C (CRT) nie jest dostępnych podczas kompilowania aplikacji platforma uniwersalna systemu Windows (platformy UWP). W niektórych przypadkach obejścia są dostępne — na przykład można użyć interfejsów API środowisko wykonawcze systemu Windows lub Win32. Jednak w innych przypadkach funkcje CRT zostały zakazane, ponieważ funkcje, które odpowiadają im lub obsługujące interfejsy API nie mają zastosowania do aplikacji platformy UWP. Aby wyszukać alternatywną metodę obsługiwaną dla środowisko wykonawcze systemu Windows, zobacz [alternatywy dla interfejsów API systemu Windows w aplikacjach platformy UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Poniższa tabela zawiera listę funkcji CRT, które nie są dostępne podczas kompilowania aplikacji platformy UWP i wskazuje wszelkie obejścia, które mają zastosowanie.

## <a name="unsupported-crt-functions"></a>Nieobsługiwane funkcje CRT

||||
|-|-|-|
|_beep _sleep _seterrormode|Te funkcje były przestarzałe w poprzednich wersjach CRT. Ponadto odpowiednie interfejsy API Win32 nie są dostępne dla aplikacji platformy UWP.|Brak obejścia.|
|chdir _chdrive getcwd|Te funkcje są przestarzałe lub nie są bezpieczne dla wątków.|Użyj _chdir, _getcwd i powiązanych funkcji.|
|_cgets _cgets_s _cgetws _cgetws_s _cprintf _cprintf_l _cprintf_p _cprintf_p_l _cprintf_s _cprintf_s_l _cputs _cputws _cscanf _cscanf_l _cscanf_s _cscanf_s_l _cwait _cwprintf _cwprintf_l _cwprintf_p _cwprintf_p_l _cwprintf_s _cwprintf_s_l _cwscanf _ cwscanf_l _cwscanf_s _cwscanf_s_l _vcprintf _vcprintf_l _vcprintf_p _vcprintf_p_l _vcprintf_s _vcprintf_s_l _vcwprintf _vcwprintf_l _vcwprintf_p _vcwprintf_p_l _vcwprintf_s _vcwprintf_s_l _getch _getch_nolock _getche _getche_nolock _getwch _ getwch_nolock _getwche _getwche_nolock _putch _putch_nolock _putwch _putwch_nolock _ungetch _ungetch_nolock _ungetwch _ungetwch_nolock _kbhit kbhit Putch cgets cprintf cputs cscanf cwait getch getche ungetch|Te funkcje są używane do odczytu i zapisu bezpośrednio z i do konsoli programu. Aplikacje platformy UWP są tylko w graficznym interfejsie użytkownika. nie obsługują one konsoli programu.|Brak obejścia.|
|getpid|Ta funkcja jest przestarzała.|Użyj _getpid lub Win32 API `GetCurrentProcessId()`.|
|_getdiskfree|Niedostępne.|Użyj `GetDiskFreeSpaceExW()`Win32 API.|
|_getdrive _getdrives|Odpowiedni interfejs API nie jest dostępny dla aplikacji platformy UWP.|Brak obejścia.|
|_inp _inpd _inpw _outp _outpd _outpw INP inpd inpw Outp outpd outpw|Operacje we/wy portu nie są obsługiwane w aplikacjach platformy UWP.|Brak obejścia.|
|_ismbcalnum _ismbcalnum_l _ismbcalpha _ismbcalpha_l _ismbcdigit _ismbcdigit_l _ismbcgraph _ismbcgraph_l _ismbchira _ismbchira_l _ismbckata _ismbckata_l _ismbcl0 _ismbcl0_l _ismbcl1 _ismbcl1_l _ismbcl2 _ismbcl2_l _ismbclegal _ismbclegal_l _ ismbclower _ismbclower_l _ismbcprint _ismbcprint_l _ismbcpunct _ismbcpunct_l _ismbcspace _ismbcspace_l _ismbcsymbol _ismbcsymbol_l _ismbcupper _ismbcupper_l _mbbtombc _mbbtombc_l _mbbtype _mbbtype_l _mbccpy _mbccpy_l _mbccpy_s _mbccpy_s_l _ mbcjistojms _mbcjistojms_l _mbcjmstojis _mbcjmstojis_l _mbclen _mbclen_l _mbctohira _mbctohira_l _mbctokata _mbctokata_l _mbctolower _mbctolower_l _mbctombb _mbctombb_l _mbctoupper _mbctoupper_l _mbsbtype _mbsbtype_l _mbscat _mbscat_l _mbscat_s _ mbscat_s_l _mbschr _mbschr_l _mbscmp _mbscmp_l _mbscoll _mbscoll_l _mbscpy _mbscpy_l _mbscpy_s _mbscpy_s_l _mbscspn _mbscspn_l _mbsdec _mbsdec_l _mbsicmp _mbsicmp_l _mbsicoll _mbsicoll_l _mbsinc _mbsinc_l _mbslen _mbslen_l _mbslwr _mbslwr_l _mbslwr_s _mbslwr_s_l _mbsnbcat _mbsnbcat_l _mbsnbcat_s _mbsnbcat_s_l _mbsnbcmp _mbsnbcmp_l _mbsnbcnt _mbsnbcnt_l _mbsnbcoll _mbsnbcoll_l _mbsnbcpy _mbsnbcpy_l _mbsnbcpy_s _mbsnbcpy_s_l _mbsnbicmp _mbsnbicmp_l _mbsnbicoll _mbsnbicoll_l _mbsnbset _mbsnbset _l _mbsnbset_s _mbsnbset_s_l _mbsncat _mbsncat_l _mbsncat_s _mbsncat_s_l _mbsnccnt _mbsnccnt_l _mbsncmp _mbsncmp_l _mbsncoll _mbsncoll_l _mbsncpy _mbsncpy_l _mbsncpy_s _mbsncpy_s_l _mbsnextc _mbsnextc_l _mbsnicmp _mbsnicmp_l _mbsnicoll _mbsnicoll_ l _mbsninc _mbsninc_l _mbsnlen _mbsnlen_l _mbsnset _mbsnset_l _mbsnset_s _mbsnset_s_l _mbspbrk _mbspbrk_l _mbsrchr _mbsrchr_l _mbsrev _mbsrev_l _mbsset _mbsset_l _mbsset_s _mbsset_s_l _mbsspn _mbsspn_l _mbsspnp _mbsspnp_l _mbsstr _mbsstr_l _mbstok _ mbstok_l _mbstok_s _mbstok_s_l _mbsupr _mbsupr_l _mbsupr_s _mbsupr_s_l is_wctype|Ciągi wielobajtowe nie są obsługiwane w aplikacjach platformy UWP.|Zamiast tego użyj ciągów Unicode.|
|_pclose _pipe _popen _wpopen|Funkcja potoku nie jest dostępna dla aplikacji platformy UWP.|Brak obejścia.|
|_resetstkoflw|Obsługa interfejsów API Win32 nie jest dostępna dla aplikacji platformy UWP.|Brak obejścia.|
|_getsystime _setsystime|Są to przestarzałe interfejsy API w poprzednich wersjach CRT. Ponadto użytkownik nie może ustawić czasu systemowego w aplikacji platformy UWP z powodu braku uprawnień.|Aby uzyskać tylko czas systemowy, użyj `GetSystemTime`Win32 API. Nie można ustawić czasu systemowego.|
|_environ _putenv _putenv_s _searchenv _searchenv_s _dupenv_s _wputenv _wputenv_s _wsearchenv getenv getenv_s putenv _wdupenv_s _wenviron _wgetenv _wgetenv_s _wsearchenv_s tzset|Zmienne środowiskowe nie są dostępne dla aplikacji platformy UWP.|Brak obejścia. Aby ustawić strefę czasową, użyj _tzset.|
|_loaddll _getdllprocaddr _unloaddll|Te funkcje były przestarzałe w poprzednich wersjach CRT. Ponadto użytkownik nie może ładować bibliotek DLL z wyjątkiem tych w tym samym pakiecie aplikacji.|Używanie interfejsów API Win32 `LoadPackagedLibrary`, `GetProcAddress`i `FreeLibrary` do ładowania i używania spakowanych bibliotek DLL.|
|_wexecl _wexecle _wexeclp _wexeclpe _wexecv _wexecve _wexecvp _wexecvpe _execl _execle _execlp _execlpe _execv _execve _execvp _execvpe _spawnl _spawnle _spawnlp _spawnlpe _spawnv _spawnve _spawnvp _spawnvpe _wspawnl _wspawnle _wspawnlp _wspawnlpe _ wspawnv _wspawnve _wspawnvp _wspawnvpe _wsystem exec execle execlp execlpe execv execve execvp execvpe spawnle spawnlp spawnlpe spawnv spawnve spawnvp spawnvpe system|Ta funkcja jest niedostępna w aplikacjach platformy UWP. Aplikacja platformy UWP nie może wywołać innej aplikacji platformy UWP lub aplikacji klasycznej.|Brak obejścia.|
|_heapwalk _heapadd _heapchk _heapset _heapused|Te funkcje są zwykle używane do pracy ze stertą. Jednak odpowiednie interfejsy API Win32 nie są obsługiwane w aplikacjach platformy UWP. Aplikacje nie mogą już tworzyć ani używać stert prywatnych.|Brak obejścia. Jednak `_heapwalk` dostępne w DEBUGOWANiu CRT tylko do celów debugowania. Nie można ich używać w aplikacjach, które są przekazywane do Microsoft Store.|

W przypadku aplikacji platformy UWP dostępne są następujące funkcje, ale powinny być używane tylko wtedy, gdy nie można używać odpowiednich interfejsów API Win32 lub środowisko wykonawcze systemu Windows — na przykład podczas przenoszenia dużych baz kodu

|||
|-|-|
|Jednobajtowe funkcje ciągów — na przykład `strcat`, `strcpy`, `strlwr`i tak dalej.|PLATFORMY UWP aplikacje w formacie Unicode, ponieważ wszystkie interfejsy API Win32 i interfejsy API środowisko wykonawcze systemu Windows, które są dostępne, korzystają tylko z zestawów znaków Unicode.  Funkcje jednobajtowe zostały pozostawione w przypadku przenoszenia dużych baz kodu, ale w przeciwnym razie powinny być stosowane odpowiednie funkcje o szerokim znaku.|
|Funkcje we/wy strumienia i niskiego poziomu plików — na przykład `fopen`, `open`i tak dalej.|Te funkcje są synchroniczne, co nie jest zalecane w przypadku aplikacji platformy UWP. W aplikacjach platformy UWP Użyj asynchronicznych interfejsów API, aby otworzyć, odczytać i zapisać w plikach, aby zapobiec zablokowaniu wątku interfejsu użytkownika. Przykładami takich interfejsów API są te, które znajdują się w klasie `Windows::Storage::FileIO`.|

## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Aplikacje ze sklepu Windows 8. x i aplikacje Windows Phone 8. x

Oprócz wspomnianych wyżej interfejsów API następujące interfejsy są niedostępne w aplikacjach do sklepu Windows 8. x i aplikacji Windows Phone 8. x.

||||
|-|-|-|
|_beginthread _beginthreadex _endthread _endthreadex|Wątki API Win32 nie są dostępne w aplikacjach do sklepu Windows 8. x.|Zamiast tego użyj `Windows Runtime Windows::System::Threading::ThreadPool` lub `concurrency::task`.|
|_chdir _wchdir _getcwd _getdcwd _wgetcwd _wgetdcwd|Koncepcja katalogu roboczego nie ma zastosowania do aplikacji ze sklepu Windows 8. x.|Zamiast tego użyj pełnych ścieżek.|
|_getpid|Ta funkcja była przestarzała w poprzednich wersjach CRT.|Użyj `GetCurrentProcessId()` Win32 API|
|_isleadbyte_l _ismbbalnum, _ismbbalnum_l, _ismbbalpha, _ismbbalpha _ismbbalpha_l _ismbbgraph _ismbbgraph_l _ismbbkalnum _ismbbkalnum_l _ismbbkana _ismbbkana_l _ismbbkprint _ismbbkprint_l _ismbbkpunct _ismbbkpunct_l _ismbblead _ ismbbprint _ismbbprint_l _ismbbpunct _ismbbpunct_l _ismbbtrail _ismbbtrail_l _ismbslead _ismbslead_l _ismbstrail _ismbstrail_l _mbsdup isleadbyte|Ciągi wielobajtowe nie są obsługiwane w aplikacjach ze sklepu Windows 8. x.|Zamiast tego użyj ciągów Unicode.|
|_tzset|Zmienne środowiskowe nie są dostępne dla aplikacji ze sklepu Windows 8. x.|Brak obejścia.|
|_get_heap_handle, _heapmin|Odpowiednie interfejsy API Win32 nie są obsługiwane w aplikacjach do sklepu Windows 8. x. Aplikacje nie mogą już tworzyć stert prywatnych.|Brak obejścia. Jednak `_get_heap_handle` jest dostępny w DEBUGOWANiu CRT tylko do celów debugowania.|
