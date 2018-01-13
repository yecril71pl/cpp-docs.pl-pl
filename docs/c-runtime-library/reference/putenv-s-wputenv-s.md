---
title: "_putenv_s —, _wputenv_s — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wputenv_s
- _putenv_s
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
apitype: DLLExport
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
dev_langs: C++
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7d55736daf6652ecbde6b0d16256ccebc206bb5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="putenvs-wputenvs"></a>_putenv_s, _wputenv_s
Tworzy, modyfikuje lub usuwa zmienne środowiskowe. Są to wersje [_putenv —, _wputenv —](../../c-runtime-library/reference/putenv-wputenv.md) , ale ma ulepszone zabezpieczenia, zgodnie z opisem w [funkcje zabezpieczeń w CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Nie można używać tego interfejsu API w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows. Aby uzyskać więcej informacji, zobacz [funkcje CRT, nie są obsługiwane z parametrem /ZW](http://msdn.microsoft.com/en-us/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Składnia  
  
```  
errno_t _putenv_s(  
   const char *name,  
   const char *value   
);  
errno_t _wputenv_s(  
   const wchar_t *name,  
   const wchar_t *value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Nazwa zmiennej środowiskowej.  
  
 `value`  
 Wartość do ustawienia zmiennej środowiskowej.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość 0 w przypadku powodzenia lub kod błędu.  
  
### <a name="error-conditions"></a>Warunki błędów  
  
|`name`|`value`|Wartość zwracana|  
|------------|-------------|------------------|  
|`NULL`|wszystkie|`EINVAL`|  
|wszystkie|`NULL`|`EINVAL`|  
  
 Jeśli jeden z warunków błąd wystąpi, te funkcje Wywołaj program obsługi nieprawidłowych parametrów, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli jest dozwolone wykonywanie, aby kontynuować, te funkcje zwracają `EINVAL` i ustaw `errno` do `EINVAL`.  
  
## <a name="remarks"></a>Uwagi  
 `_putenv_s` Funkcja dodaje nowe zmienne środowiskowe lub modyfikuje wartości istniejących zmiennych środowiskowych. Zmienne środowiskowe definiują środowisko, w którym proces jest wykonywany (na przykład domyślna ścieżka wyszukiwania dla bibliotek, które mają być połączone z programem). `_wputenv_s`jest to wersja znaków dwubajtowych `_putenv_s`; `envstring` argument `_wputenv_s` jest ciągiem znaków dwubajtowych.  
  
### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu  
  
|Procedura TCHAR.H|_Unicode — & _MBCS nie zdefiniowany|_MBCS zdefiniowano|_UNICODE zdefiniowano|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tputenv_s`|`_putenv_s`|`_putenv_s`|`_wputenv_s`|  
  
 `name`Nazwa zmiennej środowiskowej, które mają być dodane lub zmodyfikowane i `value` jest wartość zmiennej. Jeśli `name` jest już częścią środowiska, jego wartość jest zamieniana `value`; w przeciwnym razie nowy `name` zmiennej i jej `value` zostaną dodane do środowiska. Można usunąć zmienną ze środowiska, określając ciąg pusty (to znaczy "") dla `value`.  
  
 `_putenv_s`i `_wputenv_s` wpływu na środowisko lokalne dla bieżącego procesu; nie można używać ich do zmodyfikowania polecenie poziomu środowiska. Funkcje te działają tylko dla struktury danych, które są dostępne do biblioteki czasu wykonywania, a nie na środowisko "segment", który system operacyjny tworzy dla procesu. Gdy zakończenie bieżącego procesu, środowisko wraca do poziomu procesu wywołującego, które w większości przypadków jest to poziom systemu operacyjnego. Jednak modyfikacji środowiska mogą zostać przekazane do nowych procesów, które są tworzone przez `_spawn`, `_exec`, lub `system`, te nowe procesy i nowe elementy, które są dodawane przez `_putenv_s` i `_wputenv_s`.  
  
 Nie należy zmieniać wpis środowiska bezpośrednio; Zamiast tego należy użyć `_putenv_s` lub `_wputenv_s` go zmienić. W szczególności bezpośrednio zwalnianie elementów `_environ[]` globalne tablicy może spowodować nieprawidłowe pamięci, należy się zająć.  
  
 `getenv`i `_putenv_s` użyj zmiennej globalnej `_environ` dostępu do tabeli środowiska; `_wgetenv` i `_wputenv_s` użyj `_wenviron`. `_putenv_s`i `_wputenv_s` może zmienić wartość `_environ` i `_wenviron`, a tym samym unieważnienie `envp` argument `main` i `_wenvp` argument `wmain`. W związku z tym jest bezpieczniejsze w użyciu `_environ` lub `_wenviron` można uzyskać dostępu do informacji o środowisku. Aby uzyskać więcej informacji na temat relacji między `_putenv_s` i `_wputenv_s` do zmiennych globalnych, zobacz [_environ —, _wenviron —](../../c-runtime-library/environ-wenviron.md).  
  
> [!NOTE]
>  `_putenv_s` i `_getenv_s` rodzin funkcje nie są wątkowo. `_getenv_s`można zwracać wskaźnik ciągu podczas `_putenv_s` modyfikowanie ciągu i spowodować losowe awarie. Upewnij się, że wywołania te funkcje są zsynchronizowane.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|`_putenv_s`|\<stdlib.h >|  
|`_wputenv_s`|\<stdlib.h > lub \<wchar.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Przykład  
 Dla przykładu, który przedstawia sposób użycia `_putenv_s`, zobacz [getenv_s —, _wgetenv_s —](../../c-runtime-library/reference/getenv-s-wgetenv-s.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [getenv —, _wgetenv —](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [_searchenv, _wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)