---
title: "Zgłoś | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: raise
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords: Raise
dev_langs: C++
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.assetid: a3ccd3ad-f68f-4a7b-a005-c3ebfb217e8b
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 703f82f5c91cfecd65cb7ca7cf875729d9967f62
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="raise"></a>wywołaj
Wysyła sygnał do wykonywania programu.  
  
> [!NOTE]
>  Nie używaj tej metody można zamknąć [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji, z wyjątkiem testowania i debugowania scenariuszy. Programowe lub interfejsu użytkownika sposób, aby zamknąć [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikacji nie są dozwolone zgodnie z sekcji 3,6 z [wymagania dotyczące certyfikacji aplikacji systemu Windows 8](http://go.microsoft.com/fwlink/?LinkId=262889). Aby uzyskać więcej informacji, zobacz [cyklem życia aplikacji (aplikacje ze Sklepu Windows)](http://go.microsoft.com/fwlink/?LinkId=262853).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      int raise(  
int sig   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *SIG*  
 Sygnał do wywołania.  
  
## <a name="return-value"></a>Wartość zwracana  
 W przypadku powodzenia **podnieść** zwraca wartość 0. W przeciwnym wypadku zwraca wartość różną od zera.  
  
## <a name="remarks"></a>Uwagi  
 **Podnieść** funkcji wysyła *sig* do wykonywania programu. Jeśli poprzednie wywołanie **sygnału** została zainstalowana funkcja obsługi sygnału, dla *sig*, **podnieść** wykonuje tej funkcji. Nie funkcji obsługi po zainstalowaniu, domyślna akcja skojarzone z wartością sygnału *sig* jest pobierana w następujący sposób.  
  
|Sygnał|Znaczenie|Domyślny|  
|------------|-------------|-------------|  
|`SIGABRT`|Przerwania pracy|Kończy program wywołujący z kodem zakończenia 3|  
|`SIGFPE`|Błąd liczb zmiennoprzecinkowych|Kończy program wywołujący|  
|`SIGILL`|Niedozwolona instrukcja|Kończy program wywołujący|  
|`SIGINT`|CTRL + C przerwania|Kończy program wywołujący|  
|`SIGSEGV`|Dostępu do magazynu niedozwolony|Kończy program wywołujący|  
|`SIGTERM`|Zakończenie żądania wysyłane do programu|Ignoruje sygnału|  
  
 Jeśli argument nie jest prawidłową sygnału określonych powyżej, program obsługi nieprawidłowych parametrów zostanie wywołany, zgodnie z opisem w [sprawdzanie poprawności parametru](../../c-runtime-library/parameter-validation.md). Jeśli nie jest obsługiwane, funkcja ustawia `errno` do `EINVAL` i zwraca wartość różną od zera.  
  
## <a name="requirements"></a>Wymagania  
  
|Procedura|Wymagany nagłówek|  
|-------------|---------------------|  
|**Zgłoś**|\<Signal.h >|  
  
 Aby uzyskać dodatkowe informacje o zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Biblioteki  
 Wszystkie wersje [biblioteki wykonawcze języka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Proces i kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)   
 [przerwania](../../c-runtime-library/reference/abort.md)   
 [sygnał](../../c-runtime-library/reference/signal.md)