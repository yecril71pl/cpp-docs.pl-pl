---
title: Opcje polecenia EDITBIN | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- editbin
dev_langs:
- C++
helpviewer_keywords:
- EDITBIN program, options
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e4fc808f27b1d7a37e29a0f308ce51d31a9cc953
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="editbin-options"></a>Opcje EDITBIN
Aby zmodyfikować plików obiektów, plików wykonywalnych i bibliotek dołączanych dynamicznie (dll), można użyć polecenia EDITBIN. Opcje określ zmiany, które wprowadza polecenia EDITBIN.  
  
 Opcja składa się z specyfikator opcji kreski (-) lub ukośnikiem (/), a po niej nazwę opcji. Nie można stosować skrót nazw opcji. Niektóre opcje przyjmują argumentów, które są określone po dwukropkiem (:). Bez spacji i karty są dozwolone w obrębie Specyfikacja opcji. Użyj spacji lub karty do oddzielania specyfikacje opcji w wierszu polecenia. Opcja nazwy i ich argumentów — słowo kluczowe lub argumentów Nazwa pliku nie jest rozróżniana. Na przykład — wiązanie i /BIND oznaczają to samo.  
  
 Polecenia EDITBIN ma następujące opcje:  
  
|Opcja|Cel|  
|------------|-------------|  
|[/ALLOWBIND](../../build/reference/allowbind.md)|Określa, czy biblioteka DLL może być powiązana.|  
|[/ALLOWISOLATION](../../build/reference/allowisolation.md)|Określa plik DLL lub pliku wykonywalnego przeszukiwanie manifestu zachowanie.|  
|[/APPCONTAINER](../../build/reference/appcontainer.md)|Określa, czy uruchomić aplikację w kontenerze AppContainer — na przykład aplikacji platformy uniwersalnej systemu Windows.|  
|[/BIND](../../build/reference/bind.md)|Ustawia adres punktów wejścia w określonych obiektów do czasu ładowania szybkości.|  
|[/DYNAMICBASE](../../build/reference/dynamicbase.md)|Określa, czy plik DLL lub wykonywalnego obrazu może być losowo przebazowanych w trakcie ładowania przy użyciu randomizacji układu przestrzeni adresowej (ASLR).|  
|[/ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|Raporty wewnętrzne błędy do firmy Microsoft.|  
|[/HEAP](../../build/reference/heap.md)|Ustawia rozmiar sterty obrazu wykonywalnego w bajtach.|  
|[/HIGHENTROPYVA](../../build/reference/highentropyva.md)|Określa, czy plik DLL lub obrazu wykonywalnego obsługuje wysokiej entropii randomizacji układu przestrzeni adresowej (64-bitowy) (ASLR).|  
|[/INTEGRITYCHECK](../../build/reference/integritycheck.md)|Określa, czy do sprawdzenia podpisu cyfrowego w czasie ładowania.|  
|[/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|Określa, czy obiekt obsługuje adresy, które są większe niż dwa gigabajty.|  
|[/NOLOGO](../../build/reference/nologo-editbin.md)|Pomijaj transparent startowy polecenia EDITBIN.|  
|[/NXCOMPAT](../../build/reference/nxcompat.md)|Określa, czy obraz wykonywalny jest zgodny z zapobieganiem wykonywaniu danych systemu Windows.|  
|[/REBASE](../../build/reference/rebase.md)|Ustawia adres podstawowy dla określonych obiektów.|  
|[/RELEASE](../../build/reference/release.md)|Ustawia sumę kontrolną w nagłówku.|  
|[/ SECTION](../../build/reference/section-editbin.md)|Zastępuje atrybuty sekcji.|  
|[/STACK](../../build/reference/stack.md)|Ustawia rozmiar stosu obrazu wykonywalnego w bajtach.|  
|[/SUBSYSTEM](../../build/reference/subsystem.md)|Określa środowiska wykonawczego.|  
|[/SWAPRUN](../../build/reference/swaprun.md)|Określa, że obrazu wykonywalnego musi być kopiowane do pliku wymiany, a następnie uruchom stamtąd.|  
|[/TSAWARE](../../build/reference/tsaware.md)|Określa, że aplikacja jest przeznaczona do uruchamiania w środowisku wielu użytkowników.|  
|[/VERSION](../../build/reference/version.md)|Ustawia numer wersji w nagłówku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)   
 [EDITBIN — dokumentacja](../../build/reference/editbin-reference.md)