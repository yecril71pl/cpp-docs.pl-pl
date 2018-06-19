---
title: _sopen_s —, _wsopen_s — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c94219ff0b357e7627528d68938ec430fd8dc14
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418487"
---
# <a name="sopens-wsopens"></a>_sopen_s, _wsopen_s

Otwiera plik do udostępniania. Te wersje programu [_sopen — i _wsopen —](sopen-wsopen.md) zostały ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).

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
Rodzaj operacji dozwolone.

*shflag*<br/>
Rodzaj udostępnianie dozwolone.

*pmode*<br/>
Ustawienie uprawnień.

## <a name="return-value"></a>Wartość zwracana

Podano niezerowe wartości zwracanej wskazuje błąd; w takim przypadku **errno** ustawiono na jedną z następujących wartości.

|errno wartość|Warunek|
|-|-|
**EACCES**| Podana ścieżka jest katalogiem, lub plik jest tylko do odczytu, ale próbowano otwarty do zapisu.
**EEXIST —**| **_O_creat —** i **_o_excl —** flagi zostały określone, ale *filename* już istnieje.
**EINVAL —**| Nieprawidłowy *oflag*, *shflag*, lub *pmode* argumentu, lub *pfh* lub *filename* został wskaźnika o wartości null.
**EMFILE —**|Nie więcej deskryptorów plików dostępny.
**ENOENT —**|Plik lub nie można odnaleźć ścieżki.

Jeśli podano nieprawidłowy argument zostanie przekazany do funkcji, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, **errno** ustawiono **einval —** i **einval —** jest zwracany.

Aby uzyskać więcej informacji na temat tych i innych kody powrotu, zobacz [errno _doserrno —, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

W przypadku błędu -1, jest zwracany za pomocą *pfh* (chyba że *pfh* wskaźnik null).

## <a name="remarks"></a>Uwagi

**_Sopen_s —** funkcja otwiera plik określony przez *filename* i przygotowuje plik do udostępnionego odczytu lub zapisu, zgodnie z definicją w *oflag* i *shflag* . **_wsopen_s —** jest wersja znaków dwubajtowych **_sopen_s —**; *filename* argument **_wsopen_s —** jest ciągiem znaków dwubajtowych. **_wsopen_s —** i **_sopen_s —** zachowują się tak samo w przeciwnym razie wartość.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tsopen_s**|**_sopen_s**|**_sopen_s**|**_wsopen_s**|

Wyrażenie całkowite *oflag* jest tworzony przez połączenie co najmniej jedną stałą manifestu, które są zdefiniowane w \<fcntl.h >. Jeśli co najmniej dwie stałe tworzą argument *oflag*, są one połączone z operator Alternatywy ( **&#124;** ).

|*oflag* stałej|Zachowanie|
|-|-|
**_O_APPEND —**|Przenosi wskaźnika pliku koniec pliku przed każdej operacji zapisu.
**_O_BINARY —**|Otwiera plik w trybie binarnym (niezrozumiały). (Zobacz [fopen —](fopen-wfopen.md) opis trybie binarnym.)
**_O_CREAT —**|Tworzy plik i otwarcie go do zapisu. Nie ma efektu Jeśli plik określony przez *filename* istnieje. *Pmode* argumentu jest wymagany, gdy **_o_creat —** jest określona.
**_O_CREAT —** &AMP;#124; **_O_SHORT_LIVED**|Tworzy plik jako tymczasowy, a jeśli to możliwe nie mogło opróżnić na dysku. *Pmode* argumentu jest wymagany, gdy **_o_creat —** jest określona.
**_O_CREAT —** &AMP;#124; **_O_TEMPORARY**|Tworzy plik jako tymczasowy; plik zostanie usunięty po zamknięciu ostatniego deskryptorów plików. *Pmode* argumentu jest wymagany, gdy **_o_creat —** jest określona.
**_O_CREAT —**&AMP;#124; ` _O_EXCL`|Zwraca wartość błędu, jeśli plik określony przez *filename* istnieje. Ma zastosowanie tylko wtedy, gdy jest używany z **_o_creat —**.
**_O_NOINHERIT**|Uniemożliwia tworzenie deskryptora udostępnionych plików.
**_O_RANDOM**|Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostępie swobodnym z dysku.
**_O_RDONLY —**|Otwiera plik tylko odczytywanie. Nie można określić za pomocą **_o_rdwr —** lub **_o_wronly —**.
**_O_RDWR —**|Otwiera plik na odczytywanie i zapisywanie. Nie można określić za pomocą **_o_rdonly —** lub **_o_wronly —**.
**_O_SEQUENTIAL**|Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostęp sekwencyjny z dysku.
**_O_TEXT —**|Otwiera plik w trybie tekstowym (translacji). (Aby uzyskać więcej informacji, zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md) i [fopen —](fopen-wfopen.md).)
**_O_TRUNC —**|Otwiera plik i obcina go do zera length; Plik musi mieć uprawnienia do zapisu. Nie można określić za pomocą **_o_rdonly —**. **_O_trunc —** używane z **_o_creat —** otwiera istniejący plik lub tworzy plik. **Uwaga:** **_o_trunc —** flagi niszczy zawartość określonego pliku.
**_O_WRONLY —**|Otwiera plik do pisania tylko. Nie można określić za pomocą **_o_rdonly —** lub **_o_rdwr —**.
**_O_U16TEXT**|Otwiera plik w trybie Unicode UTF-16.
**_O_U8TEXT**|Otwiera plik w trybie Unicode UTF-8.
**_O_WTEXT**|Otwiera plik w trybie Unicode.

Aby określić tryb dostępu do pliku, należy określić **_o_rdonly —**, **_o_rdwr —**, lub **_o_wronly —**. Brak wartości domyślnej dla trybu dostępu.

Gdy plik jest otwarty w trybie Unicode za pomocą **_O_WTEXT**, **_O_U8TEXT**, lub **_O_U16TEXT**, wejściowe funkcji tłumaczenie dane, które jest do odczytu z pliku na dane UTF-16 przechowywane jako typ **wchar_t**. Funkcje zapisu w pliku otwartym w trybie Unicode oczekiwać buforów, które zawierają dane UTF-16, przechowywane jako typ **wchar_t**. Jeśli plik jest zakodowany jako UTF-8, UTF-16 dane są tłumaczone na UTF-8 gdy jest ona zapisywana i pliku algorytmem UTF-8 zawartości jest przekształcana na UTF-16, została przeczytana. Próba odczytu lub zapisu nieparzystą liczbę bajtów w trybie Unicode powoduje błąd sprawdzania poprawności parametru. Do odczytu lub zapisu danych przechowywanych w programie jako UTF-8, tryb tekstowe lub binarne pliku zamiast trybu Unicode. Ponosisz odpowiedzialność za wszelkie wymagane tłumaczenia kodowania.

Jeśli **_sopen_s —** jest wywoływana z **_o_wronly —** | **_o_append —** (tryb dołączania) i **_O_WTEXT**, **_O_ U16TEXT**, lub **_O_U8TEXT**, po raz pierwszy próbuje otworzyć pliku do odczytu i zapisu, przeczytaj BOM, a następnie otwórz go ponownie w celu zapisywania tylko. Jeśli otwierania pliku do odczytu i zapisu kończy się niepowodzeniem, otwiera plik do zapisywania tylko i używa wartości domyślne ustawienie trybu Unicode.

Argument *shflag* jest wyrażeniem stałym, który zawiera jeden z następujących stałych manifestu, które są zdefiniowane w \<share.h >.

|*shflag* stałej|Zachowanie|
|-|-|
**_SH_DENYRW —**|Nie zezwala na odczyt i zapis do pliku.
**_SH_DENYWR —**|Nie zezwala na dostęp do zapisu do pliku.
**_SH_DENYRD —**|Nie zezwala na dostęp do odczytu do pliku.
**_SH_DENYNO —**|Zezwoleń do odczytu i zapisu.

*Pmode* zawsze jest wymagany, w odróżnieniu od w **_sopen —**. Po określeniu **_o_creat —**, jeśli plik nie istnieje, *pmode* określa ustawienia uprawnień pliku, które są ustawione, gdy nowy plik jest zamknięte po raz pierwszy. W przeciwnym razie *pmode* jest ignorowana. *pmode* jest wyrażeniem liczby całkowitej, która zawiera jedną lub obie z manifestu stałe **_s_iwrite —** i **_s_iread —**, które są zdefiniowane w \<sys\stat.h >. Zarówno stałe są podane, są połączone z operator Alternatywy. Znaczenie *pmode* ma następującą składnię.

|*pmode*|Znaczenie|
|-|-|
**_S_IREAD —**|Dozwolone tylko odczyt.
**_S_IWRITE —**|Zapisywanie dozwolone. (W praktyce umożliwia odczytywanie i zapisywanie.)
**_S_IREAD —** &AMP;#124; **_S_IWRITE —**|Odczytywanie i zapisywanie dozwolone.

Jeśli uprawnienia do zapisu nie zostanie podany, plik jest tylko do odczytu. W systemie operacyjnym Windows wszystkie pliki są do odczytu; nie jest możliwe nadaj uprawnienia tylko do zapisu. W związku z tym tryby **_s_iwrite —** i **_s_iread —** | **_s_iwrite —** są równoważne.

**_sopen_s —** stosuje bieżącą maskę pliku uprawnień do *pmode* przed uprawnienia zostały ustawione. (Zobacz [_umask —](umask.md).)

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Opcjonalne nagłówki|
|-------------|---------------------|---------------------|
|**_sopen_s**|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>, \<share.h>|
|**_wsopen_s**|\<IO.h > lub \<wchar.h >|\<fcntl.h>, \<sys/types.h>, \<sys/stat.h>, \<share.h>|

**_sopen_s —** i **_wsopen_s —** są rozszerzenia Microsoft. Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

Zobacz przykład [_locking —](locking.md).

## <a name="see-also"></a>Zobacz także

[We/Wy niskiego poziomu](../../c-runtime-library/low-level-i-o.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_fsopen, _wfsopen](fsopen-wfsopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
