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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b02219ba0afa37fdff02b6848540064d12cd001d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229379"
---
# <a name="_sopen-_wsopen"></a>_sopen, _wsopen

Otwiera plik do udostępnienia. Dostępne są bardziej bezpieczne wersje tych funkcji: zobacz [_sopen_s, _wsopen_s](sopen-s-wsopen-s.md).

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

*Nazwa pliku*<br/>
Nazwa pliku.

*oflag*<br/>
Rodzaj operacji dozwolonych.

*shflag*<br/>
Rodzaj udostępniania jest dozwolony.

*pmode*<br/>
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca deskryptor pliku otwartego pliku.

Jeśli *filename* lub *Oflag* jest wskaźnikiem **null** lub jeśli wartość *Oflag* lub *Shflag* nie znajduje się w prawidłowym zakresie wartości, wywoływana jest procedura obsługi nieprawidłowego parametru, zgodnie z opisem w [walidacji parametru](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, te funkcje zwracają wartość-1 i ustawiają **errno** na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
| **EACCES** | Dana ścieżka jest katalogiem lub plik jest tylko do odczytu, ale podjęto próbę wykonania operacji otwierania do zapisu. |
| **EEXIST** | Określono **_O_CREAT** i **_O_EXCL** flag, ale *filename* już istnieje. |
| **EINVAL** | Nieprawidłowy argument *Oflag* lub *Shflag* . |
| **EMFILE** | Nie ma więcej dostępnych deskryptorów plików. |
| **ENOENT** | Nie znaleziono pliku lub ścieżki. |

Aby uzyskać więcej informacji na temat tych i innych kodów powrotnych, zobacz [_doserrno, errno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Uwagi

Funkcja **_sopen** otwiera plik określony przez *filename* i przygotowuje plik do odczytu lub zapisu, zgodnie z definicją *Oflag* i *Shflag*. **_wsopen** to dwubajtowa wersja **_sopen**; argument *filename* **_wsopen** jest ciągiem znaków dwubajtowych. **_wsopen** i **_sopen** zachowują się identycznie w inny sposób.

Domyślnie globalny stan tej funkcji jest objęty zakresem aplikacji. Aby to zmienić, zobacz [stan globalny w CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen**|**_sopen**|**_sopen**|**_wsopen**|

Wyrażenie liczby całkowitej *Oflag* jest tworzone przez połączenie co najmniej jednej z następujących stałych manifestu, które są zdefiniowane w \<fcntl.h> . Gdy co najmniej dwie stałe tworzą argument *Oflag*, są łączone z operatorem bitowym or ( **&#124;** ).

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

Gdy plik zostanie otwarty w trybie Unicode przy użyciu **_O_WTEXT**, **_O_U8TEXT**lub **_O_U16TEXT**, funkcje wejściowe przekładają dane odczytane z pliku do danych UTF-16 przechowywanych jako typ **`wchar_t`** . Funkcje, które zapisują do pliku otwartego w trybie Unicode, oczekują buforów zawierających dane w formacie UTF-16 przechowywane jako typ **`wchar_t`** . Jeśli plik jest zakodowany jako UTF-8, dane UTF-16 są tłumaczone na UTF-8 podczas zapisywania, a zawartość zakodowana w formacie UTF-8 jest tłumaczona na UTF-16 podczas odczytywania. Próba odczytania lub zapisania nieparzystej liczby bajtów w trybie Unicode powoduje błąd walidacji parametru. Aby odczytać lub zapisać dane, które są przechowywane w programie jako UTF-8, użyj trybu plików tekstowych lub binarnych zamiast trybu Unicode. Użytkownik jest odpowiedzialny za wszelkie wymagane tłumaczenia kodowania.

Jeśli **_sopen** jest wywoływana z **_O_WRONLY**  |  **_O_APPEND** (tryb Append) i **_O_WTEXT**, **_O_U16TEXT**lub **_O_U8TEXT**, najpierw próbuje otworzyć plik do odczytu i zapisu, odczytać BOM, a następnie otworzyć go tylko do zapisu. Jeśli otwarcie pliku do odczytu i zapisu nie powiedzie się, otwiera plik wyłącznie do zapisu i używa wartości domyślnej dla ustawienia trybu Unicode.

Argument *Shflag* jest wyrażeniem stałym składającym się z jednej z następujących stałych manifestu, które są zdefiniowane w \<share.h> .

|stała *Shflag*|Zachowanie|
|-|-|
| **_SH_DENYRW** | Nie zezwala na dostęp do odczytu i zapisu do pliku. |
| **_SH_DENYWR** | Odmawia dostępu do zapisu w pliku. |
| **_SH_DENYRD** | Odmowa dostępu do odczytu do pliku. |
| **_SH_DENYNO** | Zezwala na dostęp do odczytu i zapisu. |

Argument *PMODE* jest wymagany tylko wtedy, gdy określono **_O_CREAT** . Jeśli plik nie istnieje, *PMODE* określa ustawienia uprawnień pliku, które są ustawiane, gdy nowy plik jest zamykany po raz pierwszy. W przeciwnym razie *PMODE* jest ignorowana. *PMODE* jest wyrażeniem liczb całkowitych, które zawiera jedną lub obie stałe manifestu **_S_IWRITE** i **_S_IREAD**, które są zdefiniowane w \<sys\stat.h> . Po otrzymaniu obu stałych są one łączone z operatorem bitowym lub. Znaczenie *PMODE* jest następujące.

|*pmode*|Znaczenie|
|-|-|
| **_S_IREAD** | Dozwolony jest tylko odczyt. |
| **_S_IWRITE** | Dozwolone jest zapisanie. (W efekcie zezwala na odczyt i zapis). |
| **_S_IREAD** &#124; **_S_IWRITE** | Dozwolone odczytywanie i zapisywanie. |

Jeśli nie podano uprawnienia do zapisu, plik jest tylko do odczytu. W systemie operacyjnym Windows wszystkie pliki są odczytywane; nie można udzielić uprawnienia tylko do zapisu. W związku z tym tryby **_S_IWRITE** i **_S_IREAD**  |  **_S_IWRITE** są równoważne.

**_sopen** stosuje bieżącą maskę uprawnień pliku do *PMODE* przed ustawieniem uprawnień. (Zobacz [_umask](umask.md).)

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalny nagłówek|
|-------------|---------------------|---------------------|
|**_sopen**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen**|\<io.h> lub \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|

Aby uzyskać więcej informacji o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zapoznaj się z przykładem [_locking](locking.md).

## <a name="see-also"></a>Zobacz także

[We/wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
