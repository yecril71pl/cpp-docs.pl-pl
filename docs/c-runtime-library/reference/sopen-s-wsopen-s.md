---
title: _sopen_s, _wsopen_s
ms.date: 4/2/2020
api_name:
- _sopen_s
- _wsopen_s
- _o__sopen_s
- _o__wsopen_s
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _sopen_s
- wsopen_s
- _wsopen_s
- sopen_s
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
ms.openlocfilehash: 6c3de36482c4ffdf1ef402b4059816639014eb8b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912691"
---
# <a name="_sopen_s-_wsopen_s"></a>_sopen_s, _wsopen_s

Otwiera plik do udostępnienia. Te wersje [_sopen i _wsopen](sopen-wsopen.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w temacie [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Składnia

```C
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

### <a name="parameters"></a>Parametry

*pfh*<br/>
Dojście do pliku lub-1 w przypadku błędu.

*Nazwa pliku*<br/>
Nazwa pliku.

*oflag*<br/>
Rodzaj operacji dozwolonych.

*shflag*<br/>
Rodzaj udostępniania jest dozwolony.

*pmode*<br/>
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana różna od zera wskazuje błąd; w takim przypadku **errno** jest ustawiony na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
| **EACCES** |  Dana ścieżka jest katalogiem lub plik jest tylko do odczytu, ale podjęto próbę wykonania operacji otwierania do zapisu. |
| **EEXIST** |  Określono **_O_CREAT** i **_O_EXCL** flag, ale *filename* już istnieje. |
| **EINVAL** |  Nieprawidłowy argument *Oflag*, *Shflag*lub *PMODE* lub *PFH* lub *filename* był wskaźnikiem o wartości null. |
| **EMFILE** | Nie ma więcej dostępnych deskryptorów plików. |
| **ENOENT** | Nie znaleziono pliku lub ścieżki. |

Jeśli do funkcji jest przenoszona nieprawidłowy argument, procedura obsługi nieprawidłowego parametru jest wywoływana, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** jest ustawiona na **EINVAL** i **EINVAL** jest zwracany.

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku błędu,-1 jest zwracany przez *PFH* (chyba że *PFH* jest wskaźnikiem o wartości null).

## <a name="remarks"></a>Uwagi

Funkcja **_sopen_s** otwiera plik określony przez *filename* i przygotowuje plik do odczytu lub zapisu, zgodnie z definicją *Oflag* i *Shflag*. **_wsopen_s** to dwubajtowa wersja **_sopen_s**; argument *filename* **_wsopen_s** jest ciągiem znaków dwubajtowych. **_wsopen_s** i **_sopen_s** zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

Wyrażenie liczby całkowitej *Oflag* jest tworzone przez połączenie co najmniej jednej stałej manifestu, która jest zdefiniowana w \<fcntl. h>. Gdy co najmniej dwie stałe tworzą argument *Oflag*, są łączone z operatorem bitowym or ( **&#124;** ).

|stała *Oflag*|Zachowanie|
|-|-|
| **_O_APPEND** | Przenosi wskaźnik pliku na koniec pliku przed każdą operacją zapisu. |
| **_O_BINARY** | Otwiera plik w trybie binarnym (nieprzetłumaczonym). (Zobacz [fopen](fopen-wfopen.md) , aby zapoznać się z opisem trybu binarnego). |
| **_O_CREAT** | Tworzy plik i otwiera go do zapisu. Nie działa, jeśli istnieje plik określony przez *filename* . Argument *PMODE* jest wymagany, jeśli określono **_O_CREAT** . |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Tworzy plik jako tymczasowy, a jeśli to możliwe, nie jest opróżniany na dysk. Argument *PMODE* jest wymagany, jeśli określono **_O_CREAT** . |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Tworzy plik jako tymczasowy; plik zostanie usunięty po zamknięciu ostatniego deskryptora pliku. Argument *PMODE* jest wymagany, jeśli określono **_O_CREAT** . |
| **_O_CREAT** &#124;`_O_EXCL` | Zwraca wartość błędu, jeśli istnieje plik określony przez *nazwę* pliku. Ma zastosowanie tylko w przypadku, gdy jest używany z **_O_CREAT**. |
| **_O_NOINHERIT** | Uniemożliwia utworzenie deskryptora pliku udostępnionego. |
| **_O_RANDOM** | Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, losowy dostęp z dysku. |
| **_O_RDONLY** | Otwiera plik tylko do odczytu. Nie można określić za pomocą **_O_RDWR** lub **_O_WRONLY**. |
| **_O_RDWR** | Otwiera plik do odczytu i zapisu. Nie można określić za pomocą **_O_RDONLY** lub **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Określa, że buforowanie jest zoptymalizowane dla, ale nie ograniczone do, dostęp sekwencyjny z dysku. |
| **_O_TEXT** | Otwiera plik w trybie tekst (przetłumaczony). (Aby uzyskać więcej informacji, zobacz [plik tekstowy i tryb binarny we/wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [fopen](fopen-wfopen.md)). |
| **_O_TRUNC** | Otwiera plik i obcina jego długość do zera; plik musi mieć uprawnienia do zapisu. Nie można określić za pomocą **_O_RDONLY**. **_O_TRUNC** używany z **_O_CREAT** otwiera istniejący plik lub tworzy plik. **Uwaga:** Flaga **_O_TRUNC** niszczy zawartość określonego pliku. |
| **_O_WRONLY** | Otwiera plik tylko do zapisu. Nie można określić za pomocą **_O_RDONLY** lub **_O_RDWR**. |
| **_O_U16TEXT** | Otwiera plik w trybie Unicode UTF-16. |
| **_O_U8TEXT** | Otwiera plik w trybie Unicode UTF-8. |
| **_O_WTEXT** | Otwiera plik w trybie Unicode. |

Aby określić tryb dostępu do pliku, należy określić **_O_RDONLY**, **_O_RDWR**lub **_O_WRONLY**. Brak wartości domyślnej dla trybu dostępu.

Gdy plik jest otwierany w trybie Unicode przy użyciu **_O_WTEXT**, **_O_U8TEXT**lub **_O_U16TEXT**, funkcje wejściowe przekładają dane odczytane z pliku do danych UTF-16 przechowywanych jako **wchar_t**typu. Funkcje, które zapisują do pliku otwartego w trybie Unicode, oczekują buforów zawierających dane w formacie UTF-16 przechowywane jako typ **wchar_t**. Jeśli plik jest zakodowany jako UTF-8, dane UTF-16 są tłumaczone na UTF-8 podczas zapisywania, a zawartość zakodowana w formacie UTF-8 jest tłumaczona na UTF-16 podczas odczytywania. Próba odczytania lub zapisania nieparzystej liczby bajtów w trybie Unicode powoduje błąd walidacji parametru. Aby odczytać lub zapisać dane, które są przechowywane w programie jako UTF-8, użyj trybu plików tekstowych lub binarnych zamiast trybu Unicode. Użytkownik jest odpowiedzialny za wszelkie wymagane tłumaczenia kodowania.

Jeśli **_sopen_s** jest wywoływana z **_O_WRONLY** | **_O_APPEND** (tryb Append) i **_O_WTEXT**, **_O_U16TEXT**lub **_O_U8TEXT**, najpierw próbuje otworzyć plik do odczytu i zapisu, odczytać BOM, a następnie otworzyć go tylko do zapisu. Jeśli otwarcie pliku do odczytu i zapisu nie powiedzie się, otwiera plik wyłącznie do zapisu i używa wartości domyślnej dla ustawienia trybu Unicode.

Argument *Shflag* jest wyrażeniem stałym, które składa się z jednej z następujących stałych manifestu, które są \<zdefiniowane w udziale. h>.

|stała *Shflag*|Zachowanie|
|-|-|
| **_SH_DENYRW** | Nie zezwala na dostęp do odczytu i zapisu do pliku. |
| **_SH_DENYWR** | Odmawia dostępu do zapisu w pliku. |
| **_SH_DENYRD** | Odmowa dostępu do odczytu do pliku. |
| **_SH_DENYNO** | Zezwala na dostęp do odczytu i zapisu. |

Argument *PMODE* jest zawsze wymagany, w przeciwieństwie do **_sopen**. W przypadku określenia **_O_CREAT**, jeśli plik nie istnieje, *PMODE* określa ustawienia uprawnień pliku, które są ustawiane, gdy nowy plik jest zamykany po raz pierwszy. W przeciwnym razie *PMODE* jest ignorowana. *PMODE* jest wyrażeniem liczb całkowitych, które zawiera jedną lub obie stałe manifestu **_S_IWRITE** i **_S_IREAD**, które są zdefiniowane \<w> sys\stat.h. Po otrzymaniu obu stałych są one łączone z operatorem bitowym lub. Znaczenie *PMODE* jest następujące.

|*pmode*|Znaczenie|
|-|-|
| **_S_IREAD** | Dozwolony jest tylko odczyt. |
| **_S_IWRITE** | Dozwolone jest zapisanie. (W efekcie zezwala na odczyt i zapis). |
| **_S_IREAD** &#124; **_S_IWRITE** | Dozwolone odczytywanie i zapisywanie. |

Jeśli nie podano uprawnienia do zapisu, plik jest tylko do odczytu. W systemie operacyjnym Windows wszystkie pliki są odczytywane; nie można udzielić uprawnienia tylko do zapisu. W związku z tym tryby **_S_IWRITE** i **_S_IREAD** | **_S_IWRITE** są równoważne.

**_sopen_s** stosuje bieżącą maskę uprawnień pliku do *PMODE* przed ustawieniem uprawnień. (Zobacz [_umask](umask.md).)

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<IO. h>|\<fcntl. h>, \<sys\types.h>, \<sys\stat.h>, \<Share. h>|
|**_wsopen_s**|\<IO. h> lub \<WCHAR. h>|\<fcntl. h>, \<sys/typy. h>, \<sys/stat. h>, \<Share. h>|

**_sopen_s** i **_wsopen_s** są rozszerzeniami firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [_locking](locking.md).

## <a name="see-also"></a>Zobacz też

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
