---
title: "_fsopen —, _wfsopen — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wfsopen
- _fsopen
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
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
dev_langs:
- C++
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29ace593ec55a74db72a9bfd9d8f155055923a83
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="fsopen-wfsopen"></a>_fsopen, _wfsopen
Zostanie otwarta strumienia z udostępniania plików.  
  
## <a name="syntax"></a>Składnia  
  
```  
FILE *_fsopen(   
   const char *filename,  
   const char *mode,  
   int shflag   
);  
FILE *_wfsopen(   
   const wchar_t *filename,  
   const wchar_t *mode,  
   int shflag   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Nazwa pliku, aby otworzyć.  
  
 `mode`  
 Dozwolonego typu dostępu.  
  
 `shflag`  
 Typ udostępniania dozwolone.  
  
## <a name="return-value"></a>Wartość zwracana  
 Każda z tych funkcji zwraca wskaźnik do strumienia. Wartość wskaźnika o wartości null wskazuje błąd. Jeśli `filename` lub `mode` jest `NULL` lub pusty ciąg, te funkcje wywołanie program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `NULL` i ustaw `errno` do `EINVAL`.  
  
 Aby uzyskać więcej informacji na temat tych i innych kodów błędów, zobacz [_doserrno —, errno, _sys_errlist — i _sys_nerr —](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Uwagi  
 `_fsopen` Funkcja otwiera plik określony przez `filename` jako strumienia i przygotowuje plik kolejnych udostępnionego odczytu lub zapisu, zgodnie z definicją w trybie i `shflag` argumentów. `_wfsopen` jest to wersja znaków dwubajtowych `_fsopen`; `filename` i `mode` argumenty `_wfsopen` są ciągami znaków dwubajtowych. `_wfsopen` i `_fsopen` zachowują się tak samo w przeciwnym razie wartość.  
  
 Ciąg znaków `mode` Określa typ dostępu do żądanego pliku, jak pokazano w poniższej tabeli.  
  
|Termin|Definicja|  
|----------|----------------|  
|`"r"`|Zostanie otwarty do odczytu. Jeśli plik nie istnieje lub nie można znaleźć, `_fsopen` wywołać kończy się niepowodzeniem.|  
|`"w"`|Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.|  
|`"a"`|Zostanie otwarty do zapisu na końcu pliku (dołączanie); Tworzy plik, jeśli nie istnieje.|  
|`"r+"`|Otwiera odczytywanie i zapisywanie. (Plik musi istnieć).|  
|`"w+"`|Otwiera pusty plik na odczytywanie i zapisywanie. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.|  
|`"a+"`|Zostanie otwarty do odczytu i dołączenie; Tworzy plik, jeśli nie istnieje.|  
  
 Użyj `"w"` i `"w+"` typy z ostrożnością, zgodnie z ich zniszczyć istniejące pliki.  
  
 Gdy plik jest otwarty z `"a"` lub `"a+"` dostęp typu zapis wszystkie operacje wykonywane na końcu pliku. Może być położenia wskaźnika pliku przy użyciu `fseek` lub `rewind`, ale on jest zawsze przeniesiony z powrotem do koniec pliku przed żadnego zapisu, wykonywane są wymienione. W związku z tym nie można zastąpić istniejące dane. Gdy `"r+"`, `"w+"`, lub `"a+"` określono typ dostępu, odczytywanie i zapisywanie są dozwolone (plik jest określany jako Otwórz aktualizacji). Jednak podczas przełączania między odczytu i zapisu, musi być aktywne [fsetpos —](../../c-runtime-library/reference/fsetpos.md), [fseek](../../c-runtime-library/reference/fseek-fseeki64.md), lub [rewind](../../c-runtime-library/reference/rewind.md) operacji. Bieżąca pozycja można określić dla `fsetpos` lub `fseek` operacji, w razie potrzeby. Oprócz powyższych wartości jednego z następujących znaków może być uwzględniony w `mode` określić tryb tłumaczenia dla nowych wierszy i zarządzanie plikami.  
  
|Termin|Definicja|  
|----------|----------------|  
|`t`|Otwiera plik w trybie tekstowym (translacji). W tym trybie karetki powrotu wiersza kanału informacyjnego (CR LF) kombinacje są przekształcane na pojedynczy wiersz źródła danych (LF) na wejściu i LF znaki są tłumaczone na kombinacje CR LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako plik końcowy znak wejściowy. W plikach otwarty do odczytu lub odczytu/zapisu `_fsopen` wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli to możliwe. Jest to zrobić, ponieważ używa `fseek` i `ftell` można przenieść w pliku, który może spowodować kończy się CTRL + Z `fseek` będzie działać nieprawidłowo zbliża się koniec pliku.|  
|`b`|Otwiera plik w trybie binarnym (niezrozumiały); powyżej tłumaczenia są pomijane.|  
|`S`|Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostęp sekwencyjny z dysku.|  
|`R`|Określa, że buforowanie jest zoptymalizowana pod kątem, ale nie ograniczona do dostępie swobodnym z dysku.|  
|`T`|Określa plik jako tymczasowy. Jeśli to możliwe, nie jest opróżniany na dysku.|  
|`D`|Określa plik jako tymczasowy. Jest ono usuwane po zamknięciu ostatniego wskaźnika pliku.|  
  
 Jeśli `t` lub `b` nie została podana w `mode`, tryb tłumaczenia jest definiowana za pomocą zmiennej domyślny tryb `_fmode`. Jeśli `t` lub `b` jest prefiksem argument, funkcja kończy się niepowodzeniem i zwraca `NULL`. Omówienie trybach tekstowym i binarnym, zobacz [tekstu i we/wy binarne trybu pliku](../../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
 Argument `shflag` jest wyrażeniem stałym składające się z jednego z następujących stałych manifestu, zdefiniowane w Share.h.  
  
|Termin|Definicja|  
|----------|----------------|  
|`_SH_COMPAT`|Ustawia tryb zgodności aplikacji 16-bitowych.|  
|`_SH_DENYNO`|Zezwoleń do odczytu i zapisu.|  
|`_SH_DENYRD`|Nie zezwala na dostęp do odczytu do pliku.|  
|`_SH_DENYRW`|Nie zezwala na odczyt i zapis do pliku.|  
|`_SH_DENYWR`|Nie zezwala na dostęp do zapisu do pliku.|  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfsopen`|`_fsopen`|`_fsopen`|`_wfsopen`|  
  
## <a name="requirements"></a>Wymagania  
  
|Funkcja|Wymagany nagłówek|Opcjonalne nagłówki|  
|--------------|---------------------|----------------------|  
|`_fsopen`|\<stdio.h>|\<share.h><br /><br /> Dla manifest stałą dla `shflag` parametru.|  
|`_wfsopen`|\<stdio.h > lub \<wchar.h >|\<share.h><br /><br /> Dla manifest stałą dla `shflag` parametru.|  
  
## <a name="example"></a>Przykład  
  
```  
// crt_fsopen.c  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <share.h>  
  
int main( void )  
{  
   FILE *stream;  
  
   // Open output file for writing. Using _fsopen allows us to  
   // ensure that no one else writes to the file while we are  
   // writing to it.  
    //  
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )  
   {  
      fprintf( stream, "No one else in the network can write "  
                       "to this file until we are done.\n" );  
      fclose( stream );  
   }  
   // Now others can write to the file while we read it.  
   system( "type outfile" );  
}  
```  
  
```Output  
No one else in the network can write to this file until we are done.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../../c-runtime-library/stream-i-o.md)   
 [fclose —, _fcloseall —](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen —, _wfdopen —](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [ferror —](../../c-runtime-library/reference/ferror.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen —, _wfopen —](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen —, _wfreopen —](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [_otwórz, _wopen —](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode —](../../c-runtime-library/reference/setmode.md)   
 [_sopen, _wsopen](../../c-runtime-library/reference/sopen-wsopen.md)