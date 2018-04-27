---
title: _tempnam —, _wtempnam —, tmpnam —, _wtmpnam — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ba00c1998a41f2d17408babc87b0bf45cad689b
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam

Generowania nazw, który służy do tworzenia plików tymczasowych. Niektóre z tych funkcji bezpieczniejsze wersje są dostępne; zobacz [tmpnam_s —, _wtmpnam_s —](tmpnam-s-wtmpnam-s.md).

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

*Prefiks*<br/>
Ciąg, który będzie pre oczekującego na nazwy zwrócony przez **_tempnam —**.

*Dir*<br/>
Ścieżka używana w nazwie pliku, jeśli istnieje zmienna środowiskowa nie TMP lub TMP nie jest prawidłowym katalogiem.

*str*<br/>
Wskaźnik, będą przechowywane wygenerowana nazwa, która będzie taka sama jak nazwa zwracane przez funkcję. Jest to wygodny sposób, aby zapisać wygenerowana nazwa.

## <a name="return-value"></a>Wartość zwracana

Każda z tych funkcji zwraca wskaźnik do Nazwa wygenerowana lub **NULL** w przypadku awarii. Błąd może wystąpić przy próbie więcej niż **tmp_max —** (zobacz stdio —. H) wywołania z **tmpnam —** lub jeśli używasz **_tempnam —** i ma nieprawidłową nazwę katalogu określonym w zmiennej środowiskowej TMP i w *dir* parametru.

> [!NOTE]
> Wskaźniki zwrócony przez **tmpnam —** i **_wtmpnam —** wskaż bufory statyczne wewnętrzne. [bezpłatne](free.md) powinna być wywoływana nie można cofnąć alokacji tych wskaźników. **bezpłatne** musi być wywoływany dla wskaźników przydzielonej przez **_tempnam —** i **_wtempnam —**.

## <a name="remarks"></a>Uwagi

Każda z tych funkcji zwraca nazwę pliku, który obecnie nie istnieje. **tmpnam —** zwraca nazwę unikatową w bieżącym katalogu roboczym i **_tempnam —** można wygenerować unikatowej nazwy w katalogu innym niż bieżący. Należy zauważyć, że jeśli nazwa pliku jest pre oczekującego ukośnika odwrotnego i nie informacji ścieżki, takich jak \fname21, oznacza to, że nazwa jest nieprawidłowa dla bieżącego katalogu roboczego.

Aby uzyskać **tmpnam —**, można przechowywać tej nazwy pliku wygenerowanego w *str*. Jeśli *str* jest **NULL**, następnie **tmpnam —** pozostawia wynik w statycznej buforu wewnętrznego. W związku z tym kolejnych wywołań zniszczyć tej wartości. Nazwa wygenerowana przez **tmpnam —** składa się nazwy pliku generowanych przez program i po pierwszym wywołaniu **tmpnam —**, rozszerzenie pliku numerów sekwencyjnych w podstawowej 32 (.1 .vvu, gdy **tmp_max —**  w stdio —. H jest 32 767 znaków).

**_tempnam —** wygeneruje unikatową nazwę pliku dla katalogu wybierany przez następujące reguły:

- Jeśli zmienna środowiskowa TMP jest zdefiniowane i ustawić prawidłową nazwę katalogu, zostanie wygenerowany unikatowe nazwy plików dla katalogu określonego przez TMP.

- Jeśli zmienna środowiskowa TMP nie został zdefiniowany lub jeśli jest ustawiona na nazwę katalogu, który nie istnieje, **_tempnam —** użyje *dir* parametr jako ścieżka, dla którego wygeneruje unikatowe nazwy.

- Jeśli nie zdefiniowano zmiennej środowiskowej TMP lub jeśli jest ustawiona na nazwę katalogu, który nie istnieje, a *dir* jest **NULL** lub ustaw nazwę katalogu, który nie istnieje, **_ tempnam —** będzie używał bieżącego katalogu roboczego do generowania unikatowych nazw. Obecnie Jeśli obie TMP i *dir* określ nazwy katalogów, które nie istnieją, **_tempnam —** wywołanie funkcji zakończy się niepowodzeniem.

Nazwa zwrócony przez **_tempnam —** jest złączeniem *prefiks* i numerem sekwencyjnym zostaną połączone, aby utworzyć unikatową nazwę pliku dla określonego katalogu. **_tempnam —** generuje nazwy plików, które mają bez rozszerzenia. **_tempnam —** używa [— funkcja malloc](malloc.md) Aby przydzielić miejsce dla nazwy pliku; program jest odpowiedzialny za zwalnianie to miejsce, gdy nie jest już potrzebne.

**_tempnam —** i **tmpnam —** dojście znaków wielobajtowych argumenty ciągu zgodnie z potrzebami, rozpoznawanie wielobajtowych sekwencji znaków zgodnie ze strony kodowej OEM uzyskane automatycznie z systemu operacyjnego. **_wtempnam —** jest wersja znaków dwubajtowych **_tempnam —**; argumentów i wartości zwracanej przez **_wtempnam —** są ciągami znaków dwubajtowych. **_wtempnam —** i **_tempnam —** zachowują się tak samo, z wyjątkiem **_wtempnam —** nie obsługuje ciągów znaków wielobajtowych. **_wtmpnam —** jest wersja znaków dwubajtowych **tmpnam —**; argumentów i wartości **_wtmpnam —** są ciągami znaków dwubajtowych. **_wtmpnam —** i **tmpnam —** zachowują się tak samo, z wyjątkiem **_wtmpnam —** nie obsługuje ciągów znaków wielobajtowych.

Jeśli **_DEBUG** i **_crtdbg_map_alloc —** są zdefiniowane **_tempnam —** i **_wtempnam —** zastępuje wywołań [_tempnam — _dbg i _wtempnam_dbg —](tempnam-dbg-wtempnam-dbg.md).

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam —**|**tmpnam**|**tmpnam**|**_wtmpnam**|
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
// current working directory, then uses _tempnam to create
// a unique filename with a prefix of stq.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char* name1 = NULL;
   char* name2 = NULL;

   // Create a temporary filename for the current working directory:
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf( "%s is safe to use as a temporary file.\n", name1 );
   else
      printf( "Cannot create a unique filename\n" );

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )
      printf( "%s is safe to use as a temporary file.\n", name2 );
   else
      printf( "Cannot create a unique filename\n" );

   // When name2 is no longer needed :
   if(name2)
     free(name2);

}
```

```Output
\s1gk. is safe to use as a temporary file.
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.
```

## <a name="see-also"></a>Zobacz także

[We/Wy strumienia](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
