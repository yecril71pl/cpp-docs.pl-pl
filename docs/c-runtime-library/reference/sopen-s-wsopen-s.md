---
title: _sopen_s, _wsopen_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- sopen_s function
- _wsopen_s function
- wsopen_s function
- opening files, for sharing
- files [C++], opening
- _sopen_s function
- files [C++], sharing
ms.assetid: 059a0084-d08c-4973-9174-55e391b72aa2
ms.openlocfilehash: 1d5f35615aee058b51c0b14ff9ccd38894427b20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62355637"
---
# <a name="sopens-wsopens"></a>_sopen_s, _wsopen_s

Otwiera plik do udostępniania. Te wersje [_sopen i _wsopen —](sopen-wsopen.md) mają wzmocnienia zabezpieczeń, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Dojście do pliku, lub wartość -1 w przypadku błędu.

*Nazwa pliku*<br/>
Nazwa pliku.

*oflag*<br/>
Rodzaj dozwolone operacje.

*shflag*<br/>
Rodzaj udostępnianie dozwolone.

*pmode*<br/>
Ustawienie uprawnienia.

## <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, zwracana wartość wskazuje błąd; w takim przypadku **errno** jest ustawiony na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
| **EACCES** |  Podana ścieżka jest katalogiem, lub plik jest tylko do odczytu, ale próbowano wykonać operację Otwórz do zapisu. |
| **EEXIST** |  **_O_CREAT** i **_O_EXCL** flagi zostały określone, ale *filename* już istnieje. |
| **EINVAL** |  Nieprawidłowy *oflag*, *shflag*, lub *pmode* argument lub *pfh* lub *filename* był wskaźnikiem typu null. |
| **EMFILE** | Więcej deskryptorów plików nie dostępne. |
| **ENOENT** | Plik lub nie można odnaleźć ścieżki. |

Jeśli nieprawidłowy argument jest przekazywany do funkcji, procedura obsługi nieprawidłowego parametru zostanie wywołana, zgodnie z opisem w [Parameter Validation](../../c-runtime-library/parameter-validation.md). Jeśli wykonanie może być kontynuowane, **errno** ustawiono **EINVAL** i **EINVAL** jest zwracana.

Aby uzyskać więcej informacji na temat tych i innych kodach powrotnych, zobacz [errno, _doserrno, _sys_errlist i _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku błędu -1 jest zwracane przez *pfh* (chyba że *pfh* jest wskaźnikiem wartości null).

## <a name="remarks"></a>Uwagi

**_Sopen_s —** funkcji spowoduje otwarcie pliku określonego przez *filename* i przygotowuje go do udostępnionej odczytu lub zapisu, zgodnie z definicją *oflag* i *shflag* . **_wsopen_s —** to wersja znaku dwubajtowego **_sopen_s —**; *filename* argument **_wsopen_s —** jest ciągiem znaku dwubajtowego. **_wsopen_s —** i **_sopen_s —** zachowują się identycznie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

Wyrażenia typu całkowitego *oflag* jest tworzony przez połączenie jednej lub więcej stałych manifestu, które są zdefiniowane w \<fcntl.h >. Gdy dwa lub więcej stałych tworzą argument *oflag*, są połączone za pomocą operatora bitowego OR ( **&#124;** ).

|*oflag* stałej|Zachowanie|
|-|-|
| **_O_APPEND** | Przesuwa wskaźnik myszy plików na koniec pliku przed każdej operacji zapisu. |
| **_O_BINARY** | Otwiera plik w trybie binarnym (nieprzetłumaczonym). (Zobacz [fopen —](fopen-wfopen.md) opis trybie binarnym.) |
| **_O_CREAT** | Tworzy plik i otwiera go do zapisu. Nie obowiązuje, jeżeli plik określony przez *filename* istnieje. *Pmode* argument jest wymagany, gdy **_O_CREAT** jest określony. |
| **_O_CREAT** &#124; **_O_SHORT_LIVED** | Tworzy plik jako tymczasowy, a jeśli to możliwe nie opróżnia na dysku. *Pmode* argument jest wymagany, gdy **_O_CREAT** jest określony. |
| **_O_CREAT** &#124; **_O_TEMPORARY** | Tworzy plik jako tymczasowy; plik zostanie usunięty po zamknięciu ostatniego deskryptor pliku. *Pmode* argument jest wymagany, gdy **_O_CREAT** jest określony. |
| **_O_CREAT**&AMP;#124; ` _O_EXCL` | Zwraca wartość błędu, jeśli w pliku określonym przez *filename* istnieje. Ma zastosowanie tylko wtedy, gdy jest używane z **_O_CREAT**. |
| **_O_NOINHERIT** | Uniemożliwia tworzenie deskryptora udostępnionego pliku. |
| **_O_RANDOM** | Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu losowego do dysku. |
| **_O_RDONLY** | Otwiera plik do odczytu tylko. Nie można określić za pomocą **_O_RDWR** lub **_O_WRONLY**. |
| **_O_RDWR** | Otwiera plik na odczyt i zapis. Nie można określić za pomocą **_O_RDONLY** lub **_O_WRONLY**. |
| **_O_SEQUENTIAL** | Określa, że buforowanie jest zoptymalizowane pod kątem, ale nie ogranicza się do dostępu sekwencyjnego do dysku. |
| **_O_TEXT** | Otwiera plik w trybie tekstowym (tłumaczonym). (Aby uzyskać więcej informacji, zobacz [tekstowych i binarnych We/Wy trybu](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [fopen —](fopen-wfopen.md).) |
| **_O_TRUNC** | Otwiera plik i obcina go na wartość zero length; Plik musi mieć uprawnienia do zapisu. Nie można określić za pomocą **_O_RDONLY**. **_O_TRUNC** używane z **_O_CREAT** otwiera istniejący plik lub tworzy plik. **Uwaga:** **_O_TRUNC** flagi niszczy zawartość określonego pliku. |
| **_O_WRONLY** | Otwiera plik do zapisywania tylko. Nie można określić za pomocą **_O_RDONLY** lub **_O_RDWR**. |
| **_O_U16TEXT** | Otwiera plik w trybie Unicode UTF-16. |
| **_O_U8TEXT** | Otwiera plik w trybie Unicode UTF-8. |
| **_O_WTEXT** | Otwiera plik w trybie Unicode. |

Aby określić tryb dostępu do pliku, należy określić **_O_RDONLY**, **_O_RDWR**, lub **_O_WRONLY**. Nie ma domyślne wartości dla trybu dostępu.

Po otwarciu pliku w trybie Unicode przy użyciu **_O_WTEXT**, **_O_U8TEXT**, lub **_O_U16TEXT**, wprowadź funkcji tłumaczenia danych, które są odczytywane z pliku danych UTF-16 przechowywane jako typ **wchar_t**. Funkcje, które zapisu do pliku, który został otwarty w trybie Unicode oczekiwać buforów, które zawierają dane UTF-16 przechowywane jako typ **wchar_t**. Jeśli plik jest zakodowany w formacie UTF-8, UTF-16 dane są tłumaczone na UTF-8 są zapisywane, gdy algorytmem UTF-8 zawartości jest tłumaczony na UTF-16, została przeczytana. Podjęto próbę odczytu lub zapisu nieparzystą liczbę bajtów w trybie Unicode powoduje błąd sprawdzania poprawności parametrów. Do odczytu lub zapisu danych przechowywanych w programach w formacie UTF-8, należy użyć trybu plików tekstowych lub binarnych zamiast trybie Unicode. Odpowiedzialność za wszelkie wymagane tłumaczenia kodowania.

Jeśli **_sopen_s —** jest wywoływana z **_O_WRONLY** | **_O_APPEND** (Dołącz tryb) i **_O_WTEXT**, **_O_ U16TEXT**, lub **_O_U8TEXT**, najpierw próbuje otworzyć plik do odczytu i zapisu, odczytu BOM, a następnie otwórz go ponownie do zapisywania tylko. Jeśli otwierania pliku do odczytu i zapisu kończy się niepowodzeniem, zostanie otwarty plik do zapisywania tylko i użyje wartości domyślnej dla ustawienia trybu Unicode.

Argument *shflag* jest wyrażeniem stałym, który składa się z jednego z następujących stałych manifestu, które są zdefiniowane w \<share.h >.

|*shflag* stałej|Zachowanie|
|-|-|
| **_SH_DENYRW** | Nie zezwala na odczyt i zapis do pliku. |
| **_SH_DENYWR** | Nie zezwala na dostęp do zapisu do pliku. |
| **_SH_DENYRD** | Nie zezwala na dostęp do odczytu do pliku. |
| **_SH_DENYNO** | Zezwala uprawnienia odczytu i zapisu. |

*Pmode* argument zawsze jest wymagany, w odróżnieniu od w **_sopen**. Po określeniu **_O_CREAT**, jeśli plik nie istnieje, *pmode* określa ustawienia uprawnień pliku, które są ustawione, gdy nowy plik jest zamknięty po raz pierwszy. W przeciwnym razie *pmode* jest ignorowana. *pmode* jest wyrażeniem liczby całkowitej, która zawiera jeden lub oba stałe manifestu **_S_IWRITE** i **_S_IREAD**, które są określone w \<sys\stat.h >. Oba stałe są podane, są połączone za pomocą operatora bitowego OR. Znaczenie *pmode* jest następujący.

|*pmode*|Znaczenie|
|-|-|
| **_S_IREAD** | Dozwolone tylko odczyt. |
| **_S_IWRITE** | Zapisywanie jest dozwolone. (W praktyce pozwala na odczyt i zapis.) |
| **_S_IREAD** &#124; **_S_IWRITE** | Odczyt i zapis dozwolone. |

Jeśli uprawnienia do zapisu nie zostanie określony, plik jest tylko do odczytu. W systemie operacyjnym Windows wszystkie pliki są do odczytu; nie jest możliwe przyznać uprawnienia tylko do zapisu. W związku z tym, tryby **_S_IWRITE** i **_S_IREAD** | **_S_IWRITE** są równoważne.

**_sopen_s —** stosuje bieżące maskę uprawnień do pliku, aby *pmode* przed uprawnienia są ustawiane. (Zobacz [_umask —](umask.md).)

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen_s**|\<IO.h > lub \<wchar.h >|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|

**_sopen_s —** i **_wsopen_s —** są rozszerzeniami Microsoft. Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_locking —](locking.md).

## <a name="see-also"></a>Zobacz także

[Niskiego poziomu operacji We/Wy](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
