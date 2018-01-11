---
title: "Funkcje zabezpieczeń w CRT | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
dev_langs: C++
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce5ff232a914b929153d8dc2ea6bb0951b4ff187
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="security-features-in-the-crt"></a>Funkcje zabezpieczeń w CRT
Wiele funkcji CRT starego ma bezpieczniejsze nowszej wersji. Jeśli istnieje funkcja bezpieczny, starszej wersji mniej bezpieczne jest oznaczony jako przestarzały i nowa wersja ma `_s` sufiks ("zabezpieczenia").  
  
 W tym kontekście "przestarzałe" oznacza że nie zaleca się używania funkcji; nie oznacza to, że funkcja jest zaplanowane do usunięcia z CRT.  
  
 Bezpieczne funkcje nie uniemożliwiają lub poprawianie błędów zabezpieczeń; zamiast catch one błędy wystąpieniach. Wykonują dodatkowe kontrole dla warunków błędu, a w przypadku błędu, wywołania ich obsługi błędów (zobacz [sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md)).  
  
 Na przykład `strcpy` funkcji nie ma możliwości z informacją, jeśli ciąg, który jest ona kopiowania jest za duży dla buforu docelowego. Jednak partnera bezpiecznego `strcpy_s`, ma rozmiar buforu jako parametru, dzięki czemu można określić, czy przepełnienie buforu zostanie przeprowadzona. Jeśli używasz `strcpy_s` do skopiowania 11 znaków w buforze dziesięć znak, który błąd ze strony użytkownika; `strcpy_s` nie można rozwiązać z błędu, ale można wykryć ten błąd, informujące, wywołując program obsługi nieprawidłowych parametrów.  
  
## <a name="eliminating-deprecation-warnings"></a>Wyeliminowanie ostrzeżenia dotyczące zaniechania  
 Istnieje kilka sposobów, aby wyeliminować ostrzeżenia dotyczące zaniechania dla starszych, mniej bezpieczne funkcje. Najprostszą jest po prostu określenie `_CRT_SECURE_NO_WARNINGS` lub użyj [ostrzeżenie](../preprocessor/warning.md) pragma. Albo spowoduje wyłączenie ostrzeżenia dotyczące zaniechania, ale oczywiście nadal istnieją problemy z zabezpieczeniami, które spowodowały ostrzeżenia. Do tej pory najlepiej pozostawić amortyzacja ostrzeżenia włączone i korzystać z nowych funkcji zabezpieczeń w CRT.  
  
 W języku C++ Najprostszym sposobem, w tym celu jest użycie [Overloads szablonu bezpiecznego](../c-runtime-library/secure-template-overloads.md), który w wielu przypadkach wyeliminuje ostrzeżenia dotyczące zaniechania przez zamianę wywołania funkcji przestarzałe wywołania do nowych wersji bezpiecznym z tych funkcji. Rozważmy na przykład to przestarzała wywołanie `strcpy`:  
  
```  
char szBuf[10];   
strcpy(szBuf, "test"); // warning: deprecated   
```  
  
 Definiowanie `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` jako 1 eliminuje to ostrzeżenie, zmieniając `strcpy` wywołanie `strcpy_s`, co uniemożliwia przepełnienia buforu. Aby uzyskać więcej informacji, zobacz [Secure szablonu Overloads](../c-runtime-library/secure-template-overloads.md).  
  
 Ostatecznie przestarzałe funkcje bez przeciążenia bezpiecznych szablonów, warto, ręczne aktualizowanie swój kod, aby używać bezpiecznego wersji.  
  
 Inne źródło ostrzeżenia dotyczące zaniechania, niepowiązane z zabezpieczeniami, jest funkcje POSIX. Zamień nazwy funkcji POSIX odpowiedniki standardowe (na przykład zmienić [dostępu](../c-runtime-library/reference/access-crt.md) do [_access —](../c-runtime-library/reference/access-waccess.md)), lub wyłącz ostrzeżenia dotyczące POSIX amortyzacja, definiując `_CRT_NONSTDC_NO_WARNINGS`. Aby uzyskać więcej informacji, zobacz [przestarzałe funkcje CRT](http://msdn.microsoft.com/en-us/7e259932-c6c8-4c1a-9637-639e591681a5).  
  
## <a name="additional-security-features"></a>Dodatkowe funkcje zabezpieczeń  
 Niektóre z funkcji zabezpieczeń są następujące:  
  
-   `Parameter Validation`., Parametry przekazane do funkcji CRT są weryfikowane, w obu tych funkcji bezpiecznego i wiele wersji istniejących funkcji. Te operacje sprawdzania poprawności obejmują:  
  
    -   Sprawdzanie `NULL` wartości przekazane do funkcji.  
  
    -   Sprawdzanie wartości wyliczenia ważności.  
  
    -   Sprawdzanie, czy wartości całkowitych na wartości w prawidłowych zakresów.  
  
-   Aby uzyskać więcej informacji, zobacz [sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md).  
  
-   Program obsługi nieprawidłowych parametrów jest również dostępny do deweloperów. W przypadku napotkania nieprawidłowy parametr, zamiast potwierdzające i zamykanie aplikacji, CRT zapewnia sposób, aby sprawdzić te problemy z [_set_invalid_parameter_handler —, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)funkcji.  
  
-   `Sized Buffers`., Bezpieczne funkcje wymagają, że rozmiar buforu przekazywane do dowolnej funkcji, która zapisuje w buforze. Bezpieczne wersji sprawdzić, czy bufor jest wystarczająco duży, przed zapisaniem, co pomaga uniknąć błędów przepełnienia buforu niebezpieczne, zezwalających na wykonanie złośliwego kodu. Funkcje te zwykle zwracają `errno` wpisz kod błędu, a następnie Wywołaj program obsługi nieprawidłowych parametrów, jeśli rozmiar buforu jest za mały. Funkcje, które odczytywać bufory wejściowe, takie jak `gets`, bezpiecznego wersje, które trzeba określić maksymalny rozmiar.  
  
-   `Null termination`., Niektóre funkcje, które po lewej stronie ciągi potencjalnie z systemem innym niż zakończone mają bezpiecznego wersje, które upewnij się, że parametry są prawidłowo zakończony znakiem null.  
  
-   `Enhanced error reporting`., Bezpieczne funkcje zwracają kodów błędów z więcej informacji o błędzie nie była dostępna z istniejących funkcji. Bezpieczne funkcje i wielu istniejących funkcji teraz ustawić `errno` i często zwracać `errno` kodu typu również, aby zapewnić lepsze raportowanie błędów.  
  
-   `Filesystem security`., Plik bezpiecznego dostępu bezpiecznych plików obsługę interfejsów API we/wy w przypadku domyślnej.  
  
-   `Windows security`., Proces bezpiecznego interfejsów API wymuszać zasady zabezpieczeń i umożliwić listy kontroli dostępu, należy określić.  
  
-   `Format string syntax checking`., Nieprawidłowe ciągi zostaną wykryte, na przykład przy użyciu niepoprawnego typu pola znaków `printf` ciągi formatujące.  
  
## <a name="see-also"></a>Zobacz też  
 [Sprawdzanie poprawności parametru](../c-runtime-library/parameter-validation.md)   
 [Przeciążenia bezpiecznych szablonów](../c-runtime-library/secure-template-overloads.md)   
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)