---
title: Optymalizacja sterowana profilem | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f2d72ddda460a88830f7f7692f4c9707fa3101a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimizations"></a>Optymalizacje sterowane profilem
Funkcjonalność optymalizacji sterowanej profilem umożliwia optymalizowanie pliku wyjściowego w taki sposób, że optymalizator używa danych z przebiegów testowych pliku .exe lub .dll. Dane pokazują, jak program będzie prawdopodobnie działał w środowisku produkcyjnym.  
  
 Optymalizacje sterowane profilem są dostępne tylko dla natywnych obiektów docelowych architektur x86 i [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]. Funkcja nie działa wobec plików wyjściowych, które będą wykonywane w środowisku uruchomieniowym języka wspólnego. Nawet jeśli produkuj zestawu z mieszanym kodu natywnego i zarządzanego (Kompiluj z użyciem **/CLR**), optymalizacja sterowana profilem — nie można użyć tylko kod natywny. Próba skompilowania projektu po ustawieniu tych opcji w środowisku IDE spowoduje wystąpienie błędu kompilacji.  
  
> [!NOTE]
>  Informacje, które są zbierane z profilowania uruchomień testów spowoduje zastąpienie optymalizacji, które w przeciwnym razie będą w efekcie Jeśli określisz **/Ob**, **/OS**, lub **/Ot**. Aby uzyskać więcej informacji, zobacz [/Ob (rozszerzenie funkcji wbudowanej)](../../build/reference/ob-inline-function-expansion.md) i [/OS, /Ot (Preferuj mały kod, Preferuj szybki kod)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).  
  
 Umożliwia automatyczne Optymalizacja sterowana profilem w języku Visual C++ wtyczki w Centrum diagnostyki i wydajności uprościć i usprawnić proces optymalizacji w programie Visual Studio, lub wykonaj kroki optymalizacji ręcznie w programie Visual Studio lub w Wiersz polecenia. Firma Microsoft zaleca wtyczki, ponieważ możliwe jest łatwiejsze do użycia. Aby uzyskać informacje o tym, jak pobrać wtyczki i użyć go do optymalizowania aplikacji, zobacz [wtyczek optymalizacji opartej na profilu](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md).  
  
 Zarówno profilowana Optymalizacja wtyczki i ręczne Optymalizacja sterowana profilem — wykonaj następujące kroki, aby zoptymalizować aplikacji:  
  
-   Kompiluj jeden lub więcej plików kodu źródłowego z [/GL](../../build/reference/gl-whole-program-optimization.md).  
  
     Każdy moduł skompilowany z użyciem opcji /GL może być badany w trakcie przebiegów testowych optymalizacji sterowanej profilem, aby zarejestrować jego zachowanie w czasie wykonania. Moduły w kompilacji o optymalizacji sterowanej profilem nie muszą być kompilowane z opcją /GL. Jednak tylko moduły skompilowane przy użyciu tej opcji będą instrumentowane i później dostępne dla optymalizacji sterowanych profilem.  
  
-   Połącz przy użyciu [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) i [opcji/genprofile](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).  
  
     Używając opcji/genprofile i opcję/LTCG tworzy plik .pgd puste. Po dodaniu danych z przebiegów testowych do pliku .pgd mogą one służyć jako dane wejściowe następnego kroku łączenia (tworzenie zoptymalizowanego obrazu). Podczas określania opcji/genprofile, można opcjonalnie dodawać: PGD =`filename` można określić niestandardowy nazwę lub lokalizację pliku .pgd.  
  
-   Wykonaj profilowanie aplikacji.  
  
     Każde kończenia sesji PROFILOWANEGO EXE lub PROFILOWANEGO biblioteki DLL jest zwolniony, *appname*! zostanie utworzony plik # .pgc. Plik .pgc zawiera informacje o konkretnym przebiegu testowym aplikacji. # jest liczbą, począwszy od 1, która zwiększa się na podstawie liczby innych *appname*! # .pgc plików w katalogu. Plik .pgc można usunąć, jeśli przebieg testowy nie reprezentuje scenariusza, który ma być optymalizowany.  
  
     Podczas uruchomienia testu, można wymusić zamknięcia .pgc aktualnie otwarty plik i utworzenie nowego pliku .pgc z [pgosweep](../../build/reference/pgosweep.md) narzędzia (na przykład, gdy koniec scenariusza testu nie pokrywa się z zamykania aplikacji).  
  
     Podczas profilowania aplikacji można użyć opcji `PogoSafeMode`. Ta opcja pozwala określić, czy aplikacja ma być profilowana w trybie awaryjnym czy szybkim. Aby uzyskać więcej informacji na temat trybów, zobacz [PogoSafeMode](../../build/reference/pogosafemode.md).  
  
-   Połącz przy użyciu opcję/LTCG i /USEPROFILE.  
  
     Używając opcję/LTCG i /USEPROFILE tworzy zoptymalizowanego obrazu. W tym kroku danymi wejściowymi jest plik .pgd. Podczas określania /USEPROFILE, można opcjonalnie dodawać: PGD =`filename` można określić niestandardowy nazwę lub lokalizację pliku .pgd. Aby uzyskać więcej informacji, zobacz [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  
  
 Można nawet utworzyć zoptymalizowany plik wyjściowy, a następnie stwierdzić, że przydałoby się dodatkowe profilowanie w celu utworzenia bardziej zoptymalizowanego obrazu. Jeśli instrumentowany obraz i jego plik .pgd są dostępne, można wykonać dodatkowe przebiegi testowe i ponownie skompilować zoptymalizowany obraz przy użyciu nowszego pliku .pgd.  
  
 Oto lista optymalizacji sterowanych profilem:  
  
-   **Ze śródwierszowaniem** — na przykład, jeśli istnieje funkcja A czy często wywołania funkcji B i funkcja B jest stosunkowo mały, a następnie funkcja wbudowana B w funkcji A. będzie optymalizacje sterowane profilem  
  
-   **Wirtualne spekulacji wywołać** -wywołanie wirtualnych lub innych połączeń za pomocą wskaźnika funkcji jest często przeznaczony dla niektórych funkcji, optymalizacja sterowana profilem — można wstawić warunkowo wykonywane bezpośrednie wywołanie funkcji często docelowe i bezpośrednie wywołanie może być wbudowane.  
  
-   **Zarejestruj alokacji** — Optymalizowanie z wynikami danych profilu w lepsze alokacja rejestru.  
  
-   **Podstawowe optymalizacji bloku** -optymalizacji bloku podstawowego umożliwia często wykonywane podstawowych bloków, które tymczasowo wykonywane w ramach danego ramkę, która będzie umieszczona w tym samym zestawie stron (miejscowości). Zmniejsza to liczbę używanych stron, a w efekcie obciążenie pamięci.  
  
-   **Optymalizacja rozmiaru i szybkość** — funkcje, których program zużywa dużo czasu może być zoptymalizowany pod kątem szybkości.  
  
-   **Funkcja układu** — oparte na wykresu wywołań i profilowane zachowanie wywołujący/wywoływany, funkcje, które są w tej samej ścieżce wykonywania są umieszczane w tej samej sekcji.  
  
-   **Warunkowe optymalizacji gałęzi** — z sondy wartość profilowana optymalizacje można znaleźć, jeśli danej wartości w instrukcji switch służy częściej niż innych wartości.  Następnie taką wartość można usunąć z instrukcji switch.  Analogicznie można postąpić z instrukcjami if/else. Optymalizator będzie umieszczał na początku blok „if” lub „else” w zależności od tego, który z nich częściej generuje wartość „true”.  
  
-   **Martwy separacją kodu** -kod, który nie jest wywoływana podczas profilowania zostanie przeniesiony do specjalnej sekcji dołączany na końcu zestawu sekcji. To wygodny sposób utrzymania tej sekcji poza często używanymi stronami.  
  
-   **EH separacją kodu** -wyjątkowo wykonywany, kod EH często mogą zostać przeniesione do osobnej sekcji, gdy optymalizacje sterowane profilem można określić, czy wyjątki występować tylko w wyjątkowych warunków.  
  
-   **Funkcje wewnętrzne pamięci** — rozszerzenie funkcje wewnętrzne może zostać podjęta lepiej, jeśli można określić, czy wewnętrzna nazywa się często. Funkcję wewnętrzną można również optymalizować na podstawie rozmiaru bloku operacji przenoszenia i kopiowania.  
  
 Aby uzyskać więcej informacji na wykonywanie optymalizacji ręcznego w IDE lub w wierszu polecenia, zobacz [wtyczek optymalizacji opartej na profilu](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wtyczka do optymalizacji profilowej](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)  
  
 [Narzędzia do ręcznej optymalizacji sterowanej profilem](../../build/reference/tools-for-manual-profile-guided-optimization.md)  
  
 [Instrukcje: scalanie wielu profili PGO w jeden profil](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia kompilacji C/C++](../../build/reference/c-cpp-build-tools.md)