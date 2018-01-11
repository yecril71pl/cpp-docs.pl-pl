---
title: "_putenv —, _wputenv — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
dev_langs: C++
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 509766f9f324c1dd9488488861e7c64200d44837
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="putenv-wputenv"></a>_putenv, _wputenv
Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Bezpieczniejsza wersje te funkcje są dostępne; zobacz [_putenv_s —, _wputenv_s —](../../c-runtime-library/reference/putenv-s-wputenv-s.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
int _putenv(  
   const char *envstring   
);  
int _wputenv(  
   const wchar_t *envstring   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `envstring`  
 Definicja ciągu środowiska.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca 0 w przypadku powodzenia lub wartość -1 w przypadku błędu.  
  
## <a name="remarks"></a>Uwagi  
 `_putenv` Funkcja dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym proces jest wykonywany (na przykład domyślna ścieżka wyszukiwania dla bibliotek, które mają być połączone z programem). `_wputenv`jest to wersja znaków dwubajtowych `_putenv`; `envstring` argument `_wputenv` jest ciągiem znaków dwubajtowych.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura tchar.h|_UNICODE i _MBCS niezdefiniowane|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tputenv`|`_putenv`|`_putenv`|`_wputenv`|  
  
 `envstring` Argument musi być wskaźnikiem do ciągu w postaci `varname=string`, gdzie `varname` to nazwa zmiennej środowiskowej, które mają być dodane lub zmodyfikowane i `string` jest wartość zmiennej. Jeśli `varname` jest już częścią środowiska, jego wartość jest zamieniana `string`; w przeciwnym razie nowy `varname` zmiennej i jej `string` wartości zostaną dodane do środowiska. Można usunąć zmienną ze środowiska, określając pustą `string` — innymi słowy, określając tylko `varname=`.  
  
 `_putenv`i `_wputenv` wpływu na środowisko lokalne dla bieżącego procesu; nie można używać ich do zmodyfikowania polecenie poziomu środowiska. Oznacza to, że funkcje te działają tylko na dostęp do biblioteki wykonawczej struktury danych, a nie na segment środowiska tworzone przez system operacyjny dla procesu. Gdy zakończenie bieżącego procesu, środowisko wraca do poziomu procesu wywołującego (w większości przypadków poziomu systemu operacyjnego). Jednak modyfikacji środowiska mogą być przekazywane wszystkie nowe procesy utworzone przez `_spawn`, `_exec`, lub `system`, i wszelkie nowe elementy dodane przez te nowe procesy `_putenv` i `_wputenv`.  
  
 Nie należy zmieniać wpis środowiska bezpośrednio: Użyj `_putenv` lub `_wputenv` go zmienić. W szczególności zwalnianie bezpośrednie elementy `_environ[]` globalne tablicy może doprowadzić do nieprawidłowej pamięci adresowane.  
  
 `getenv`i `_putenv` użyj zmiennej globalnej `_environ` dostępu do tabeli środowiska; `_wgetenv` i `_wputenv` użyj `_wenviron`. `_putenv`i `_wputenv` może zmieniać wartość `_environ` i `_wenviron`, w związku z tym unieważnienia `_envp` argument `main` i `_wenvp` argument `wmain`. W związku z tym jest bezpieczniejsze w użyciu `_environ` lub `_wenviron` można uzyskać dostępu do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji programu `_putenv` i `_wputenv` do zmiennych globalnych, zobacz [_environ —, _wenviron —](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  `_putenv` i `_getenv` rodzin funkcje nie są wątkowo. `_getenv`można zwracać wskaźnik ciągu podczas `_putenv` modyfikuje ciągu znaków powoduje losowe awarie. Upewnij się, że wywołania te funkcje są zsynchronizowane.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_putenv`|\<stdlib.h >|  
|`_wputenv`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać więcej informacji o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Przykładowe zastosowania `_putenv`, zobacz [getenv —, _wgetenv —](../../c-runtime-library/reference/getenv-wgetenv.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [getenv —, _wgetenv —](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_searchenv, _wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)