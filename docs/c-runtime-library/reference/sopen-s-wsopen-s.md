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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 81feacae0e4608512e7325c57e7f2b96bcf2cdde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356505"
---
# <a name="_sopen_s-_wsopen_s"></a>_sopen_s, _wsopen_s

Otwiera plik do udostępniania. Te wersje [_sopen i _wsopen](sopen-wsopen.md) mają ulepszenia zabezpieczeń, zgodnie z opisem w funkcji zabezpieczeń w [CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Pfh*<br/>
Dojście do pliku lub -1 w przypadku błędu.

*Pod nazwą*<br/>
Nazwa pliku.

*żużel*<br/>
Rodzaj operacji dozwolone.

*żużel*<br/>
Rodzaj udostępniania dozwolone.

*pmode*<br/>
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Wartość zwracana niezerowa wskazuje błąd; w takim przypadku **errno** jest ustawiona na jedną z następujących wartości.

|wartość errno|Warunek|
|-|-|
| **EACCES ( EACCES )** |  Dana ścieżka jest katalogiem lub plik jest tylko do odczytu, ale podjęto próbę operacji otwartego do zapisu. |
| **EEXIST (EEXIST)** |  **określono flagi _O_CREAT** i **_O_EXCL,** ale *nazwa pliku* już istnieje. |
| **Einval** |  Nieprawidłowy *oflag*, *shflag*, lub *argument pmode* lub *pfh* lub *nazwa pliku* był wskaźnik null. |
| **EMFILE (EMFILE)** | Nie ma już dostępnych deskryptorów plików. |
| **Enoent** | Nie znaleziono pliku lub ścieżki. |

Jeśli nieprawidłowy argument jest przekazywany do funkcji, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [weryfikacji parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, **errno** jest ustawiona na **EINVAL** i **EINVAL** jest zwracany.

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku błędu -1 jest zwracany przez *pfh* (chyba że *pfh* jest wskaźnikiem null).

## <a name="remarks"></a>Uwagi

Funkcja **_sopen_s** otwiera plik określony przez *nazwę pliku* i przygotowuje plik do wspólnego odczytu lub zapisu, zgodnie z *definicją oflag* i *shflag*. **_wsopen_s** jest szerokoznakową wersją **_sopen_s**; *argumentnazyt,* który **ma _wsopen_s** jest ciągiem znaków o szerokim charakterze. **_wsopen_s** i **_sopen_s** zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

Wyrażenie całkowite *oflag* jest tworzone przez połączenie jednej lub więcej stałych \<manifestu, które są zdefiniowane w fcntl.h>. Gdy dwa lub więcej stałych tworzą argument *oflag*, są one łączone z operatorem bitowym-OR ( **&#124;** ).

|stała *oflag*|Zachowanie|
|-|-|
| **_O_APPEND** | Przenosi wskaźnik pliku na koniec pliku przed każdą operacją zapisu. |
| **_O_BINARY** | Otwiera plik w trybie binarnym (nieprzetłumaczonym). (Opis trybu binarnego można znaleźć w [opisie](fopen-wfopen.md) trybu binarnego). |
| **_O_CREAT** | Tworzy plik i otwiera go do zapisu. Nie ma wpływu, jeśli plik określony przez *nazwę pliku* istnieje. Argument *pmode* jest wymagany, gdy **określono _O_CREAT.** |
| **_O_CREAT** **&#124; _O_SHORT_LIVED** | Tworzy plik jako tymczasowy i jeśli to możliwe nie jest równokiem na dysku. Argument *pmode* jest wymagany, gdy **określono _O_CREAT.** |
| **_O_CREAT** **&#124; _O_TEMPORARY** | Tworzy plik jako tymczasowy; plik zostanie usunięty po zamknięciu ostatniego deskryptora pliku. Argument *pmode* jest wymagany, gdy **określono _O_CREAT.** |
| **_O_CREAT** &#124;`_O_EXCL` | Zwraca wartość błędu, jeśli istnieje plik określony przez *nazwę pliku.* Ma zastosowanie tylko w przypadku użycia z **_O_CREAT**. |
| **_O_NOINHERIT** | Zapobiega tworzeniu deskryptora udostępnionego pliku. |
| **_O_RANDOM** | Określa, że buforowanie jest zoptymalizowane pod kątem losowego dostępu z dysku, ale nie ogranicza się do niego. |
| **_O_RDONLY** | Otwiera plik tylko do odczytu. Nie można określić za pomocą **_O_RDWR** lub **_O_WRONLY**. |
| **_O_RDWR** | Otwiera plik do odczytu i zapisu. Nie można określić za pomocą **_O_RDONLY** lub **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Określa, że buforowanie jest zoptymalizowane pod kątem sekwencyjnego dostępu z dysku, ale nie ogranicza się do niego. |
| **_O_TEXT** | Otwiera plik w trybie tekstowym (przetłumaczonym). (Aby uzyskać więcej informacji, zobacz [Tekst i tryb binarny plik We/Wy](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [fopen](fopen-wfopen.md).) |
| **_O_TRUNC** | Otwiera plik i obcina go do zerowej długości; plik musi mieć uprawnienie do zapisu. Nie można określić za pomocą **_O_RDONLY**. **_O_TRUNC** używany z **_O_CREAT** otwiera istniejący plik lub tworzy plik. **Uwaga:** Flaga **_O_TRUNC** niszczy zawartość określonego pliku. |
| **_O_WRONLY** | Otwiera plik tylko do zapisu. Nie można określić za pomocą **_O_RDONLY** lub **_O_RDWR**. |
| **_O_U16TEXT** | Otwiera plik w trybie Unicode UTF-16. |
| **_O_U8TEXT** | Otwiera plik w trybie Unicode UTF-8. |
| **_O_WTEXT** | Otwiera plik w trybie Unicode. |

Aby określić tryb dostępu do pliku, należy określić **_O_RDONLY** **, _O_RDWR**lub **_O_WRONLY**. Nie ma żadnej wartości domyślnej dla trybu dostępu.

Gdy plik jest otwierany w trybie Unicode przy użyciu **_O_WTEXT**, **_O_U8TEXT**lub **_O_U16TEXT,** funkcje wejściowe tłumaczą dane odczytane z pliku na dane UTF-16 przechowywane jako **typ wchar_t**. Funkcje zapisu, które zapisują do pliku otwartego w trybie Unicode, oczekują buforów zawierających dane UTF-16 przechowywane jako **typ wchar_t**. Jeśli plik jest zakodowany jako UTF-8, następnie UTF-16 dane są tłumaczone na UTF-8, gdy jest zapisywany, a plik UTF-8 zakodowane zawartość jest tłumaczona na UTF-16, gdy jest odczytywany. Próba odczytu lub zapisu nieparzystej liczby bajtów w trybie Unicode powoduje błąd sprawdzania poprawności parametru. Aby odczytać lub zapisać dane przechowywane w programie jako UTF-8, użyj trybu tekstowego lub binarnego zamiast trybu Unicode. Użytkownik jest odpowiedzialny za wszelkie wymagane tłumaczenie kodowania.

Jeśli **_sopen_s** jest wywoływana z **_O_WRONLY** | **_O_APPEND** (tryb dołączania) i **_O_WTEXT**, **_O_U16TEXT**lub **_O_U8TEXT,** najpierw próbuje otworzyć plik do odczytu i zapisu, odczytać BOM, a następnie ponownie otworzyć go tylko do zapisu. Jeśli otwarcie pliku do odczytu i zapisu nie powiedzie się, otwiera plik tylko do zapisu i używa wartości domyślnej dla ustawienia trybu Unicode.

Argument *shflag* jest wyrażeniem stałym, które składa się z jednej \<z następujących stałych manifestu, które są zdefiniowane w share.h>.

|stała *shflag*|Zachowanie|
|-|-|
| **_SH_DENYRW** | Odmawia dostępu do odczytu i zapisu do pliku. |
| **_SH_DENYWR** | Odmawia dostępu do zapisu do pliku. |
| **_SH_DENYRD** | Odmawia dostępu do odczytu do pliku. |
| **_SH_DENYNO** | Zezwala na dostęp do odczytu i zapisu. |

Argument *pmode* jest zawsze wymagany, w przeciwieństwie do **_sopen**. Po określeniu **_O_CREAT**, jeśli plik nie istnieje, *pmode* określa ustawienia uprawnień pliku, które są ustawiane, gdy nowy plik jest zamknięty po raz pierwszy. W przeciwnym razie *pmode* jest ignorowany. *pmode* jest wyrażeniem liczby całkowitej, które zawiera jedną lub obie stałe manifestu **_S_IWRITE** \<i **_S_IREAD**, które są zdefiniowane w> sys\stat.h. Gdy obie stałe są podane, są one łączone z operatorem bitowym-OR. Znaczenie *pmode* jest w następujący sposób.

|*pmode*|Znaczenie|
|-|-|
| **_S_IREAD** | Dozwolone tylko czytanie. |
| **_S_IWRITE** | Pisanie dozwolone. (W efekcie pozwala na czytanie i pisanie). |
| **_S_IREAD _S_IWRITE** &#124; **&#124;** | Czytanie i pisanie dozwolone. |

Jeśli uprawnienie do zapisu nie jest podane, plik jest tylko do odczytu. W systemie operacyjnym Windows wszystkie pliki są czytelne; nie można udzielić uprawnień tylko do zapisu. W związku z tym tryby **_S_IWRITE** i **_S_IWRITE** | **_S_IREAD** są równoważne.

**_sopen_s** stosuje bieżącą maskę uprawnień do pliku do *pmode* przed ustawieniem uprawnień. (Zobacz [_umask](umask.md).)

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<> io.h|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen_s**|\<io.h> lub \<wchar.h>|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|

**_sopen_s** i **_wsopen_s** są rozszerzeniami firmy Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_locking](locking.md).

## <a name="see-also"></a>Zobacz też

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
