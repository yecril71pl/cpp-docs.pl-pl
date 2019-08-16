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
ms.openlocfilehash: 0e8e11182948e9bccf1c55685cc7c3d55ff697c8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500764"
---
# <a name="_tempnam-_wtempnam-tmpnam-_wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam

Generuj nazwy, których można użyć do tworzenia plików tymczasowych. Bardziej bezpieczne wersje niektórych z tych funkcji są dostępne; Zobacz [tmpnam_s, _wtmpnam_s](tmpnam-s-wtmpnam-s.md).

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
Ciąg, który będzie wstępnie oczekiwał na nazwy zwrócone przez **_tempnam**.

*katalogów*<br/>
Ścieżka użyta w nazwie pliku, jeśli nie istnieje zmienna środowiskowa TMP lub jeśli TMP nie jest prawidłowym katalogiem.

*str*<br/>
Wskaźnik, który będzie przechowywać wygenerowaną nazwę i będzie taka sama jak nazwa zwrócona przez funkcję. Jest to wygodny sposób zapisania wygenerowanej nazwy.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do wygenerowanej nazwy lub **wartości null** , jeśli wystąpił błąd. Błąd może wystąpić, Jeśli podjęto próbę więcej niż **TMP_MAX** (patrz stdio. H) wywołania z **tmpnam** lub w przypadku używania **_tempnam** , w zmiennej środowiskowej tmp i w parametrze *dir* jest określona Nieprawidłowa nazwa katalogu.

> [!NOTE]
> Wskaźniki zwracane przez **tmpnam** i **_wtmpnam** wskazują wewnętrzne bufory statyczne. [](free.md) nie należy wywoływać bezpłatnej, aby cofnąć te wskaźniki. należy wywołać **bezpłatne** dla wskaźników przyznanych przez **_tempnam** i **_wtempnam**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zwraca nazwę pliku, który obecnie nie istnieje. **tmpnam** zwraca nazwę, która jest unikatowa w wydzielonym katalogu tymczasowym systemu Windows zwróconym przez [GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw). tempnam generuje unikatową nazwę w katalogu innym niż wyznaczono.  **\_** Zwróć uwagę, że nazwa pliku jest wstępnie zainstalowana z ukośnikiem odwrotnym i bez informacji o ścieżce, takich jak \fname21, oznacza to, że nazwa jest prawidłowa dla bieżącego katalogu roboczego.

W przypadku **tmpnam**można zapisać tę wygenerowaną nazwę pliku w *str*. Jeśli *str* ma **wartość null**, **tmpnam** pozostawia wynik w wewnętrznym buforze statycznym. W ten sposób wszystkie kolejne wywołania powodują zniszczenie tej wartości. Nazwa wygenerowana przez **tmpnam** składa się z nazwy pliku generowanej przez program i, po pierwszym wywołaniu do **tmpnam**, rozszerzenie pliku numerów sekwencyjnych w podstawowej 32 (. 1-. vvu, gdy **TMP_MAX** w stdio. H to 32 767).

**_tempnam** wygeneruje unikatową nazwę pliku dla katalogu wybranego przez następujące reguły:

- Jeśli zmienna środowiskowa TMP jest zdefiniowana i ma ustawioną prawidłową nazwę katalogu, dla katalogu określonego przez TMP należy generować unikatowe nazwy plików.

- Jeśli zmienna środowiskowa TMP nie jest zdefiniowana lub jeśli jest ustawiona na nazwę katalogu, który nie istnieje, **_tempnam** użyje parametru *dir* jako ścieżki, dla której zostaną wygenerowane unikatowe nazwy.

- Jeśli zmienna środowiskowa TMP nie jest zdefiniowana lub jest ustawiona na nazwę katalogu, który nie istnieje, a jeśli *dir* ma **wartość null** lub jest ustawiona na nazwę katalogu, który nie istnieje, **_tempnam** będzie używać bieżącego katalogu roboczego do genu Oceń unikatowe nazwy. Obecnie Jeśli zarówno TMP, jak i *dir* określają nazwy katalogów, które nie istnieją, wywołanie funkcji **_tempnam** zakończy się niepowodzeniem.

Nazwa zwrócona przez **_tempnam** będzie łączyć *prefiks* i numer sekwencyjny, który zostanie połączony w celu utworzenia unikatowej nazwy pliku dla określonego katalogu. **_tempnam** generuje nazwy plików, które nie mają rozszerzenia. **_tempnam** używa [malloc](malloc.md) do przydzielenia miejsca na nazwę pliku; Program jest odpowiedzialny za zwolnienie tego miejsca, gdy nie jest już potrzebne.

**_tempnam** i **tmpnam** automatycznie obsługują argumenty ciągu znaków wielobajtowych, aby rozpoznawać sekwencje znaków wielobajtowych zgodnie ze stroną kodową OEM uzyskaną z systemu operacyjnego. **_wtempnam** to dwubajtowa wersja **_tempnam**; argumenty i wartość zwracana przez **_wtempnam** są ciągami znaków dwubajtowych. **_wtempnam** i **_tempnam** zachowują się identycznie, z tą różnicą, że **_wtempnam** nie obsługują ciągów znaków wielobajtowych. **_wtmpnam** to dwubajtowa wersja **tmpnam**; argument i wartość zwracana przez **_wtmpnam** są ciągami znaków dwubajtowych. **_wtmpnam** i **tmpnam** zachowują się identycznie, z tą różnicą, że **_wtmpnam** nie obsługują ciągów znaków wielobajtowych.

Jeśli **_DEBUG** i **_CRTDBG_MAP_ALLOC** są zdefiniowane, **_tempnam** i **_wtempnam** są zastępowane przez wywołania [_tempnam_dbg i _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|Nie zdefiniowano _UNICODE & _MBCS|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**, **_wtmpnam**|\<stdio. h > lub \<WCHAR. h >|
|**tmpnam**|\<stdio.h>|

Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodność](../../c-runtime-library/compatibility.md).

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

[We/wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
