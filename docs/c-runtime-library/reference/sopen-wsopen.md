---
title: _sopen, _wsopen
ms.date: 4/2/2020
api_name:
- _sopen
- _wsopen
- _o__sopen
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
- _wsopen
- wsopen
- _sopen
- _tsopen
helpviewer_keywords:
- sopen function
- sharing files
- opening files, for sharing
- _sopen function
- wsopen function
- files [C++], opening
- files [C++], sharing
- _wsopen function
ms.assetid: a9d4cccf-06e9-414d-96fa-453fca88cc1f
ms.openlocfilehash: 0ee788823b62d97cdc81e901a812ba25f40359e9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356402"
---
# <a name="_sopen-_wsopen"></a>_sopen, _wsopen

Otwiera plik do udostępniania. Dostępne są bezpieczniejsze wersje tych funkcji: patrz [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

## <a name="syntax"></a>Składnia

```C
int _sopen(
   const char *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
int _wsopen(
   const wchar_t *filename,
   int oflag,
   int shflag [,
   int pmode ]
);
```

### <a name="parameters"></a>Parametry

*Pod nazwą*<br/>
Nazwa pliku.

*żużel*<br/>
Rodzaj operacji dozwolone.

*żużel*<br/>
Rodzaj udostępniania dozwolone.

*pmode*<br/>
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca deskryptora pliku dla otwartego pliku.

Jeśli *nazwa pliku* lub *oflag* jest wskaźnikiem **NULL** lub jeśli *oflag* lub *shflag* nie mieści się w prawidłowym zakresie wartości, wywoływany jest nieprawidłowy program obsługi parametrów, zgodnie z opisem w [polu Sprawdzanie poprawności parametrów.](../../c-runtime-library/parameter-validation.md) Jeśli wykonanie jest dozwolone, te funkcje zwracają -1 i ustawić **errno** do jednej z następujących wartości.

|wartość errno|Warunek|
|-|-|
| **EACCES ( EACCES )** | Dana ścieżka jest katalogiem lub plik jest tylko do odczytu, ale podjęto próbę operacji otwartego do zapisu. |
| **EEXIST (EEXIST)** | **określono flagi _O_CREAT** i **_O_EXCL,** ale *nazwa pliku* już istnieje. |
| **Einval** | Nieważny argument *oflag* lub *shflag.* |
| **EMFILE (EMFILE)** | Nie ma już dostępnych deskryptorów plików. |
| **Enoent** | Nie znaleziono pliku lub ścieżki. |

Aby uzyskać więcej informacji na temat tych i innych kodów zwrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_sopen** otwiera plik określony przez *nazwę pliku* i przygotowuje plik do wspólnego odczytu lub zapisu, zgodnie z *definicją oflag* i *shflag*. **_wsopen** jest szerokoznakową wersją **_sopen**; *argumentnazyt,* który **ma _wsopen** jest ciągiem znaków o szerokim charakterze. **_wsopen** i **_sopen** zachowują się identycznie w przeciwnym razie.

Domyślnie stan globalny tej funkcji jest ograniczony do aplikacji. Aby to zmienić, zobacz [Stan globalny w crt](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

Wyrażenie całkowite *oflag* jest tworzone przez połączenie jednej lub więcej następujących stałych manifestu, które są zdefiniowane w \<fcntl.h>. Gdy dwa lub więcej stałych tworzą argument *oflag*, są one łączone z operatorem bitowym-OR ( **&#124;** ).

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

Jeśli **_sopen** jest wywoływana z **_O_WRONLY** | **_O_APPEND** (tryb dołączania) i **_O_WTEXT**, **_O_U16TEXT**lub **_O_U8TEXT,** najpierw próbuje otworzyć plik do odczytu i zapisu, odczytać BOM, a następnie ponownie otworzyć go tylko do zapisu. Jeśli otwarcie pliku do odczytu i zapisu nie powiedzie się, otwiera plik tylko do zapisu i używa wartości domyślnej dla ustawienia trybu Unicode.

Argument *shflag* jest wyrażeniem stałym składającym się z jednej z \<następujących stałych manifestu, które są zdefiniowane w share.h>.

|stała *shflag*|Zachowanie|
|-|-|
| **_SH_DENYRW** | Odmawia dostępu do odczytu i zapisu do pliku. |
| **_SH_DENYWR** | Odmawia dostępu do zapisu do pliku. |
| **_SH_DENYRD** | Odmawia dostępu do odczytu do pliku. |
| **_SH_DENYNO** | Zezwala na dostęp do odczytu i zapisu. |

Argument *pmode* jest wymagany tylko wtedy, gdy **określono _O_CREAT.** Jeśli plik nie istnieje, *pmode* określa ustawienia uprawnień pliku, które są ustawiane po pierwszym zamknięciu nowego pliku. W przeciwnym razie *pmode* jest ignorowany. *pmode* jest wyrażeniem liczby całkowitej, które zawiera jedną lub obie stałe manifestu **_S_IWRITE** \<i **_S_IREAD**, które są zdefiniowane w> sys\stat.h. Gdy obie stałe są podane, są one łączone z operatorem bitowym-OR. Znaczenie *pmode* jest w następujący sposób.

|*pmode*|Znaczenie|
|-|-|
| **_S_IREAD** | Dozwolone tylko czytanie. |
| **_S_IWRITE** | Pisanie dozwolone. (W efekcie pozwala na czytanie i pisanie). |
| **_S_IREAD _S_IWRITE** &#124; **&#124;** | Czytanie i pisanie dozwolone. |

Jeśli uprawnienie do zapisu nie jest podane, plik jest tylko do odczytu. W systemie operacyjnym Windows wszystkie pliki są czytelne; nie można udzielić uprawnień tylko do zapisu. W związku z tym tryby **_S_IWRITE** i **_S_IWRITE** | **_S_IREAD** są równoważne.

**_sopen** stosuje bieżącą maskę uprawnień do pliku do *pmode* przed ustawieniem uprawnień. (Zobacz [_umask](umask.md).)

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_sopen**|\<> io.h|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen**|\<io.h> lub \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [Zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_locking](locking.md).

## <a name="see-also"></a>Zobacz też

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
