---
title: _tempnam, _wtempnam, tmpnam, _wtmpnam
ms.date: 11/04/2016
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
ms.openlocfilehash: 29fa8fc836b1b52bcf66247b3f6aaba47b8c2eaa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284874"
---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam

Generowanie nazwy, których można użyć, aby utworzyć pliki tymczasowe. Bardziej bezpieczne wersje niektórych z tych funkcji są dostępne; zobacz [tmpnam_s —, _wtmpnam_s —](tmpnam-s-wtmpnam-s.md).

## <a name="syntax"></a>Składnia

```C
char *_tempnam(
   const char *dir,
   const char *prefix
);
wchar_t *_wtempnam(
   const wchar_t *dir,
   const wchar_t *prefix
);
char *tmpnam(
   char *str
);
wchar_t *_wtmpnam(
   wchar_t *str
);
```

### <a name="parameters"></a>Parametry

*prefix*<br/>
Ciąg, który będzie pre oczekującego nazw zwróconych przez **_tempnam —**.

*dir*<br/>
Ścieżka użyte w nazwie pliku, jeśli zmienna środowiskowa nie TMP lub TMP nie jest prawidłowym katalogiem.

*str*<br/>
Wskaźnik będzie przechowywać wygenerowaną nazwę, która będzie taka sama jak nazwa, zwrócona przez funkcję. Jest to wygodny sposób, aby zapisać wygenerowaną nazwę.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do nazwy wygenerowanej lub **NULL** w przypadku awarii. Błąd może wystąpić, jeśli użytkownik podejmie więcej niż **TMP_MAX** (zobacz stdio —. H) wywołań w przypadku **tmpnam —** lub jeśli używasz **_tempnam —** i ma nieprawidłową nazwę katalogu określonego w zmiennej środowiskowej TMP i w *dir* parametru.

> [!NOTE]
> Wskaźniki zwrócony przez **tmpnam —** i **_wtmpnam —** wskaż bufory statyczne wewnętrzne. [bezpłatne](free.md) nie powinna być wywoływana należy cofnąć te wskaźniki. **bezpłatne** musi być wywoływany dla wskaźników przydzielonej przez **_tempnam —** i **_wtempnam —**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zwraca nazwę pliku, który obecnie nie istnieje. **tmpnam —** zwraca nazwę, która jest unikatowa w wyznaczonym katalog tymczasowy Windows zwracane przez [GetTempPathW](/windows/desktop/api/fileapi/nf-fileapi-gettemppathw). **\_tempnam —** generuje unikatową nazwę w katalogu innym niż wyznaczone. Należy zauważyć, że jeśli nazwa pliku jest pre oczekującego ukośnik odwrotny i żadnych informacji o ścieżce, takie jak \fname21, oznacza to, że nazwa jest nieprawidłowa dla bieżącego katalogu roboczego.

Aby uzyskać **tmpnam —**, możesz zapisać tę nazwę wygenerowanego pliku w *str*. Jeśli *str* jest **NULL**, następnie **tmpnam —** pozostawia wynik w statycznych buforu wewnętrznego. Ten sposób kolejnych wywołań zniszczyć tę wartość. Nazwa wygenerowana przez **tmpnam —** zawiera nazwę pliku wygenerowanego przez program, a po pierwszym wywołaniu **tmpnam —**, rozszerzenie pliku numerów sekwencyjnych w podstawowej 32 (.1 .vvu, gdy **TMP_MAX**  w stdio —. H jest 32 767 znaków).

**_tempnam —** wygeneruje unikatową nazwę pliku dla katalogu, w wybranym przez następujące reguły:

- Jeśli zmienna środowiskowa TMP jest zdefiniowane i Ustaw prawidłową nazwę katalogu, zostanie wygenerowany unikatowych nazw plików dla katalogu określonego przez TMP.

- Jeśli nie zdefiniowano zmiennej środowiskowej TMP lub jeśli jest ustawiona na nazwę katalogu, który nie istnieje, **_tempnam —** użyje *dir* parametr jako ścieżki, dla którego zostanie wygenerowany unikatowe nazwy.

- Jeśli nie zdefiniowano zmiennej środowiskowej TMP lub jeśli jest ustawiona na nazwę katalogu, który nie istnieje, a *dir* jest **NULL** lub ustawić na nazwę katalogu, który nie istnieje, **_ tempnam —** będzie używał do bieżącego katalogu roboczego do generowania unikatowych nazw. Obecnie Jeśli obie TMP i *dir* określić nazwy katalogów, które nie istnieją, **_tempnam —** wywołanie funkcji zakończy się niepowodzeniem.

Nazwę zwróconą przez **_tempnam —** będzie składa się z *prefiks* i numerem sekwencyjnym będą łączone, aby utworzyć unikatową nazwę pliku do określonego katalogu. **_tempnam —** generuje nazw plików, które mają bez rozszerzenia. **_tempnam —** używa [— funkcja malloc](malloc.md) do alokowania miejsca dla nazwy pliku; program jest odpowiedzialny za zwalnianie to miejsce, gdy nie jest już potrzebny.

**_tempnam —** i **tmpnam —** automatycznie uchwyt znaków wielobajtowych argumenty typu string zgodnie z potrzebami, rozpoznawaniu sekwencje znaków wielobajtowych według stronę kodową OEM uzyskaną od systemu operacyjnego. **_wtempnam —** to wersja znaku dwubajtowego **_tempnam —**; argumenty i wartość zwracana przez **_wtempnam —** są ciągami znaków dwubajtowych. **_wtempnam —** i **_tempnam —** zachowują się identycznie, chyba że **_wtempnam —** nie obsługuje ciągi znaków wielobajtowych. **_wtmpnam —** to wersja znaku dwubajtowego **tmpnam —**; argument i wartość zwracana przez **_wtmpnam —** są ciągami znaków dwubajtowych. **_wtmpnam —** i **tmpnam —** zachowują się identycznie, chyba że **_wtmpnam —** nie obsługuje ciągi znaków wielobajtowych.

Jeśli **_DEBUG** i **_CRTDBG_MAP_ALLOC** są zdefiniowane, **_tempnam —** i **_wtempnam —** są zastępowane przez wywołania [_tempnam — _dbg i _wtempnam_dbg —](tempnam-dbg-wtempnam-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_UNICODE & _MBCS nie zdefiniowano|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam —**, **_wtmpnam —**|\<stdio.h > lub \<wchar.h >|
|**tmpnam**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Przykład

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// temporary directory, and _tempname to create a unique filename
// in C:\\tmp.

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
   char * name1 = NULL;
   char * name2 = NULL;
   char * name3 = NULL;

   // Create a temporary filename for the current working directory:
   if ((name1 = tmpnam(NULL)) != NULL) { // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf("%s is safe to use as a temporary file.\n", name1);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if ((name2 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name2);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // When name2 is no longer needed:
   if (name2) {
      free(name2);
   }

   // Unset TMP environment variable, then create a temporary filename in C:\tmp.
   if (_putenv("TMP=") != 0) {
      printf("Could not remove TMP environment variable.\n");
   }

   // With TMP unset, we will use C:\tmp as the temporary directory.
   // Create a temporary filename in C:\tmp with prefix "stq".
   if ((name3 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name3);
   }
   else {
      printf("Cannot create a unique filename\n");
   }

   // When name3 is no longer needed:
   if (name3) {
      free(name3);
   }

   return 0;
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\sriw.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\stq2 is safe to use as a temporary file.
c:\tmp\stq3 is safe to use as a temporary file.
```

## <a name="see-also"></a>Zobacz także

[Stream operacji We/Wy](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
