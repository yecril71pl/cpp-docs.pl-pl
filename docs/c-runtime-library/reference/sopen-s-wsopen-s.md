---
title: "_sopen_s —, _wsopen_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _sopen_s
- _wsopen_s
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _sopen_s
- wsopen_s
- _wsopen_s
- sopen_s
dev_langs:
- C++
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 67bc88f047806e21245389837b9f712d3491033a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="sopens-wsopens"></a>_sopen_s, _wsopen_s
Otwiera plik do udostępniania. Te wersje programu [_sopen — i _wsopen —](../../c-runtime-library/reference/sopen-wsopen.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _sopen_s(  
   int* pfh,  
   const char *filename,  
   int oflag,  
   int shflag,  
   int pmode  
);  
errno_t _wsopen_s(  
   int* pfh,  
   const wchar_t *filename,  
   int oflag,  
   int shflag,  
   int pmode,  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `pfh`  
 Dojście do pliku, lub wartość -1 w przypadku błędu.  
  
 [in] `filename`  
 Nazwa pliku.  
  
 [in] `oflag`  
 Rodzaj operacji dozwolone.  
  
 [in] `shflag`  
 Rodzaj udostępnianie dozwolone.  
  
 [in] `pmode`  
 Ustawienie uprawnień.  
  
## <a name="return-value"></a>Wartość zwracana  
 Podano niezerowe wartości zwracanej wskazuje błąd; w takim przypadku `errno` ustawiono na jedną z następujących wartości.  
  
 `EACCES`  
 Podana ścieżka jest katalogiem, lub plik jest tylko do odczytu, ale próbowano otwarty do zapisu.  
  
 `EEXIST`  
 `_O_CREAT` i `_O_EXCL` flagi zostały określone, ale `filename` już istnieje.  
  
 `EINVAL`  
 Nieprawidłowy `oflag`, `shflag`, lub `pmode` argumentu, lub `pfh` lub `filename` został wskaźnika o wartości null.  
  
 `EMFILE`  
 Nie więcej deskryptorów plików dostępny.  
  
 `ENOENT`  
 Plik lub nie można odnaleźć ścieżki.  
  
 Jeśli podano nieprawidłowy argument zostanie przekazany do funkcji, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, `errno` ustawiono `EINVAL` i `EINVAL` jest zwracany.  
  
 Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 W przypadku błędu -1, jest zwracany za pomocą `pfh` (chyba że `pfh` wskaźnik null).  
  
## <a name="remarks"></a>Uwagi  
 `_sopen_s` Funkcja otwiera plik określony przez `filename` i przygotowuje plik do udostępnionego odczytu lub zapisu, zgodnie z definicją w `oflag` i `shflag`. `_wsopen_s` jest to wersja znaków dwubajtowych `_sopen_s`; `filename` argument `_wsopen_s` jest ciągiem znaków dwubajtowych. `_wsopen_s` i `_sopen_s` zachowują się tak samo w przeciwnym razie wartość.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tsopen_s`|`_sopen_s`|`_sopen_s`|`_wsopen_s`|  
  
 Wyrażenie całkowite `oflag` jest tworzony przez połączenie co najmniej jedną stałą manifestu, które są zdefiniowane w \<fcntl.h >. Jeśli co najmniej dwie stałe tworzą argument `oflag`, są one połączone z operator Alternatywy ( `|` ).  
  
 `_O_APPEND`  
 Zmienia położenie pliku wskaźnik na koniec pliku przed każdej operacji zapisu.  
  
 `_O_BINARY`  
 Otwiera plik w trybie binarnym (niezrozumiały). (Zobacz [fopen —](../../c-runtime-library/reference/fopen-wfopen.md) opis trybie binarnym.)  
  
 `_O_CREAT`  
 Tworzy plik i otwarcie go do zapisu. Nie ma efektu Jeśli plik określony przez `filename` istnieje.  
  
 `_O_CREAT | _O_SHORT_LIVED`  
 Tworzy plik jako tymczasowy, a jeśli to możliwe nie mogło opróżnić na dysku.  
  
 `_O_CREAT | _O_TEMPORARY`  
 Tworzy plik jako tymczasowy; plik zostanie usunięty po zamknięciu ostatniego deskryptorów plików.  
  
 `_O_CREAT | _O_EXCL`  
 Zwraca wartość błędu, jeśli plik określony przez `filename` istnieje. Ma zastosowanie tylko wtedy, gdy jest używany z `_O_CREAT`.  
  
 `_O_NOINHERIT`  
 Uniemożliwia tworzenie deskryptora udostępnionych plików.  
  
 `_O_RANDOM`  
 Określa przede wszystkim na dostępie z dysku.  
  
 `_O_RDONLY`  
 Otwiera plik tylko odczytywanie. Nie można określić za pomocą `_O_RDWR` lub `_O_WRONLY`.  
  
 `_O_RDWR`  
 Otwiera plik na odczytywanie i zapisywanie. Nie można określić za pomocą `_O_RDONLY` lub `_O_WRONLY`.  
  
 `_O_SEQUENTIAL`  
 Określa głównie dostęp sekwencyjny z dysku.  
  
 `_O_TEXT`  
 Otwiera plik w trybie tekstowym (translacji). (Aby uzyskać więcej informacji, zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [fopen —](../../c-runtime-library/reference/fopen-wfopen.md).)  
  
 `_O_TRUNC`  
 Otwiera plik i obcina go do zera length; Plik musi mieć uprawnienia do zapisu. Nie można określić za pomocą `_O_RDONLY`. `_O_TRUNC` używane z `_O_CREAT` otwiera istniejący plik lub tworzy plik.  
  
> [!NOTE]
>  `_O_TRUNC` Flagi niszczy zawartość określonego pliku.  
  
 `_O_WRONLY`  
 Otwiera plik do pisania tylko. Nie można określić za pomocą `_O_RDONLY` lub `_O_RDWR`.  
  
 `_O_U16TEXT`  
 Otwiera plik w trybie Unicode UTF-16.  
  
 `_O_U8TEXT`  
 Otwiera plik w trybie Unicode UTF-8.  
  
 `_O_WTEXT`  
 Otwiera plik w trybie Unicode.  
  
 Aby określić tryb dostępu do pliku, należy określić `_O_RDONLY`, `_O_RDWR`, lub `_O_WRONLY`. Brak wartości domyślnej dla trybu dostępu.  
  
 Gdy plik jest otwarty w trybie Unicode za pomocą `_O_WTEXT`, `_O_U8TEXT`, lub `_O_U16TEXT`, wejściowe funkcji tłumaczenie dane, które jest do odczytu z pliku do przechowywane jako typ danych UTF-16 `wchar_t`. Funkcje zapisu w pliku otwartym w trybie Unicode oczekiwać buforów, które zawierają dane UTF-16, przechowywane jako typ `wchar_t`. Jeśli plik jest zakodowany jako UTF-8, UTF-16 dane są tłumaczone na UTF-8 gdy jest ona zapisywana i pliku algorytmem UTF-8 zawartości jest przekształcana na UTF-16, została przeczytana. Próba odczytu lub zapisu nieparzystą liczbę bajtów w trybie Unicode powoduje błąd sprawdzania poprawności parametru. Do odczytu lub zapisu danych przechowywanych w programie jako UTF-8, tryb tekstowe lub binarne pliku zamiast trybu Unicode. Ponosisz odpowiedzialność za wszelkie wymagane tłumaczenia kodowania.  
  
 Jeśli `_sopen_s` jest wywoływana z `_O_WRONLY | _O_APPEND` (tryb dołączania) i `_O_WTEXT`, `_O_U16TEXT`, lub `_O_U8TEXT`, po raz pierwszy próbuje otworzyć pliku do odczytu i zapisu, przeczytaj BOM, a następnie otwórz go ponownie w celu zapisywania tylko. Jeśli otwierania pliku do odczytu i zapisu kończy się niepowodzeniem, otwiera plik do zapisywania tylko i używa wartości domyślne ustawienie trybu Unicode.  
  
 Argument `shflag` jest wyrażeniem stałym, który zawiera jeden z następujących stałych manifestu, które są zdefiniowane w \<share.h >.  
  
 `_SH_DENYRW`  
 Nie zezwala na odczyt i zapis do pliku.  
  
 `_SH_DENYWR`  
 Nie zezwala na dostęp do zapisu do pliku.  
  
 `_SH_DENYRD`  
 Nie zezwala na dostęp do odczytu do pliku.  
  
 `_SH_DENYNO`  
 Zezwoleń do odczytu i zapisu.  
  
 `pmode` Zawsze jest wymagany, w odróżnieniu od w `_sopen`. Po określeniu `_O_CREAT`, jeśli plik nie istnieje, `pmode` określa ustawienia uprawnień pliku, które są ustawione, gdy nowy plik jest zamknięte po raz pierwszy. W przeciwnym razie `pmode` jest ignorowana. `pmode` jest wyrażeniem liczby całkowitej, która zawiera jedną lub obie z manifestu stałe `_S_IWRITE` i `_S_IREAD`, które są zdefiniowane w \<sys\stat.h >. Zarówno stałe są podane, są połączone z operator Alternatywy. Znaczenie `pmode` ma następującą składnię.  
  
 `_S_IWRITE`  
 Zapisywanie dozwolone.  
  
 `_S_IREAD`  
 Odczytywanie dozwolone.  
  
 `_S_IREAD | _S_IWRITE`  
 Odczytywanie i zapisywanie dozwolone.  
  
 Jeśli uprawnienia do zapisu nie zostanie podany, plik jest tylko do odczytu. W systemie operacyjnym Windows wszystkie pliki są do odczytu; nie jest możliwe nadaj uprawnienia tylko do zapisu. W związku z tym tryby `_S_IWRITE` i `_S_IREAD | _S_IWRITE` są równoważne.  
  
 `_sopen_s` stosuje bieżący maskę pliku uprawnień do `pmode` przed uprawnienia zostały ustawione. (Zobacz [_umask —](../../c-runtime-library/reference/umask.md).)  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|  
|-------------|---------------------|---------------------|  
|`_sopen_s`|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|  
|`_wsopen_s`|\<IO.h > lub \<wchar.h >|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|  
  
 `_sopen_s` i `_wsopen_s` są rozszerzenia Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [_locking —](../../c-runtime-library/reference/locking.md).  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)   
 [_zamknij](../../c-runtime-library/reference/close.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_fsopen, _wfsopen](../../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)