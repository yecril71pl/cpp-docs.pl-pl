---
title: "-sdl (Włącz dodatkowe testy zabezpieczeń) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCCLCompilerTool.SDLCheck
dev_langs: C++
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5cbcb74272fa7cae3dd0c641bd6371c8f0f9c204
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (Włącz dodatkowe kontrole zabezpieczeń)
Dodaje zalecane kontroli Security Development Lifecycle (SDL). Kontrole te obejmują bardzo związanych z zabezpieczeniami ostrzeżenia jako błędy i funkcje dodatkowe bezpiecznego generowania kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
/sdl[-]  
```  
  
## <a name="remarks"></a>Uwagi  
 **/ SDL** włącza nadzbiór kontroli zabezpieczeń linii bazowej, które są udostępniane przez [/GS](../../build/reference/gs-buffer-security-check.md) i zastępuje **/GS-**. Domyślnie **/SDL** jest wyłączona. **Zgłaszanie** wyłącza sprawdzanie dodatkowe zabezpieczenia.  
  
## <a name="compile-time-checks"></a>Sprawdzenie w czasie kompilacji  
 **/ SDL** włącza te ostrzeżenia jako błędy:  
  
|Ostrzeżenie włączane przez/SDL|Odpowiednik przełącznik wiersza polecenia|Opis|  
|------------------------------|-------------------------------------|-----------------|  
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|Jednoargumentowy minus operator została zastosowana do typu unsigned, co w wyniku bez znaku.|  
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|Ujemne stałe całkowite skonwertowano na typ bez znaku, co w wyniku prawdopodobnie znaczenia.|  
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|Użycie `continue`, `break` lub `goto` słów kluczowych w `__finally` / `finally` bloku ma niezdefiniowane zachowanie podczas przerwania pracy.|  
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|Inicjowanie zmiennej kod nie zostanie wykonany.|  
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|Użycie niezainicjowanej zmiennej lokalnej.|  
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|Użycie potencjalnie niezainicjowanej lokalnej zmiennej wskaźnikowej.|  
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|Przepełnienie stosowania określone funkcje (CRT) wykonawcze języka C buforu.|  
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|Używać funkcji oznaczonych pragma [przestarzałe](../../preprocessor/deprecated-c-cpp.md).|  
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|Używać funkcji oznaczona jako [przestarzałe](../../cpp/deprecated-cpp.md).|  
  
## <a name="runtime-checks"></a>Sprawdzanie czasu wykonania  
 Gdy **/SDL** jest włączone, kompilator generuje kod do wykonania tych testów w czasie wykonywania:  
  
-   Włącza tryb strict **/GS** wykrywania przepełnienie buforu czasu wykonywania, odpowiednikiem kompilowania przy użyciu `#pragma strict_gs_check(push, on)`.  
  
-   Wykonuje ich oczyszczania ograniczone wskaźnika. W wyrażeniach, które nie wymagają wyłuskań i typy, których nie ma destruktora zdefiniowane przez użytkownika, odwołania do wskaźnika są ustawione nie jest prawidłowym adresem po wywołaniu `delete`. Pozwala to zapobiec ponownemu użyciu odwołania do starych wskaźnika.  
  
-   Wykonuje inicjowanie elementu członkowskiego klasy. Automatycznie inicjuje wszystkich elementów członkowskich klasy na zero dla wystąpienia obiektu (przed uruchomieniem Konstruktora). Pomaga to zapobiec użycia niezainicjowanej dane skojarzone z elementów członkowskich klasy, które nie jawnie zainicjować konstruktora.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [ostrzeżenia, / SDL i poprawy niezainicjowanej zmiennej wykrywania](http://go.microsoft.com/fwlink/p/?LinkId=331012).  
  
#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Na **ogólne** wybierz tę opcję z **kontroli SDL** listy rozwijanej.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)