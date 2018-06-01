---
title: 'Porady: porządkowanie plików wyjściowych projektu dla kompilacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5058493e93a89e64c87ef52b73ff8fe3272f8f99
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705348"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Porady: porządkowanie plików wyjściowych projektu dla kompilacji
W tym temacie opisano najlepsze rozwiązania dotyczące porządkowanie plików wyjściowych projektu. Tworzenie mogą wystąpić błędy podczas konfigurowania plików wyjściowych projektu niepoprawnie. W tym temacie opisano także zalety i wady każdej alternatywę do organizowania plików wyjściowych projektu.  
  
## <a name="referencing-clr-assemblies"></a>Odwołania do zestawów CLR  
  
#### <a name="to-reference-assemblies-with-using"></a>Do zestawów odwołań z #using  
  
1.  Możesz odwoływać się do zestawu bezpośrednio w kodzie za pomocą #using — dyrektywa, takich jak `#using <System.Data.dll>`. Aby uzyskać więcej informacji, zobacz [# dyrektywa using](../preprocessor/hash-using-directive-cpp.md).  
  
     Określony plik może być .dll, .exe, modułu .netmodule lub .obj, tak długo, jak jest MSIL. Składnika mogą być tworzone w dowolnym języku. Przy użyciu tej opcji, konieczne będzie dostęp do funkcji IntelliSense, ponieważ metadane zostaną wyodrębnione ze MSIL. W pliku musi być w ścieżce projektu. w przeciwnym razie projekt nie zostanie skompilowany i IntelliSense będzie niedostępna. Kliknij prawym przyciskiem myszy jest prosty sposób określić, czy plik jest w ścieżce #using wiersza i wybierz polecenie **Otwórz dokument** polecenia. Jeśli nie można odnaleźć pliku, otrzymasz powiadomienie.  
  
     Jeśli nie chcesz umieścić pełną ścieżkę do pliku, możesz użyć **/AI** — opcja kompilatora można edytować ścieżkę wyszukiwania dla #using. Aby uzyskać więcej informacji, zobacz [/AI (Określ katalogi metadanych)](../build/reference/ai-specify-metadata-directories.md).  
  
#### <a name="to-reference-assemblies-with-fu"></a>Aby odwołać się do zestawów z /FU  
  
1.  Zamiast odwołania do zestawu bezpośrednio z pliku kodu, jak opisano powyżej, możesz użyć **/FU** — opcja kompilatora. Zaletą tej metody jest, że nie trzeba dodać osobną # instrukcję using do każdego pliku, który odwołuje się do danego zestawu.  
  
     Aby ustawić tę opcję, należy otworzyć **stron właściwości** dla projektu. Rozwiń węzeł **właściwości konfiguracji** węzeł, a następnie rozwiń węzeł **C/C++** a następnie wybierz węzeł **zaawansowane**. Dodaj odpowiednie zestawy obok pozycji **życie #using**. Aby uzyskać więcej informacji, zobacz [/FU (nazwij wymuszone #using)](../build/reference/fu-name-forced-hash-using-file.md).  
  
#### <a name="to-reference-assemblies-with-add-new-reference"></a>Aby odwołać zestawy z Dodaj nowe odwołanie  
  
1.  Jest to najprostszy sposób używać zestawów CLR. Najpierw upewnij się, że projekt został skompilowany przy **/CLR** — opcja kompilatora. Następnie kliknij prawym przyciskiem myszy projekt z **Eksploratora rozwiązań** i wybierz **Dodaj**, **odwołania**. **Strony właściwości** wyświetli się okno dialogowe.  
  
2.  Z **strony właściwości** okno dialogowe, wybierz opcję **Dodaj nowe odwołanie**. Okno dialogowe pojawi się lista wszystkich .NET, COM i innych zestawów, które są dostępne w bieżącym projekcie. Wybierz żądany zestaw, a następnie kliknij przycisk **OK**.  
  
     Po ustawieniu odwołania projektu odpowiadające im zależności są realizowane automatycznie. Ponadto ponieważ metadane są częścią zestawu, nie jest nie trzeba dodawać pliku nagłówka lub prototypu elementy, które są używane z zarządzanych zestawów.  
  
## <a name="referencing-native-dlls-or-static-libraries"></a>Odwołanie do natywnych bibliotek DLL lub biblioteki statyczne  
  
#### <a name="to-reference-native-dlls-or-static-libraries"></a>Aby odwołać natywnych bibliotek DLL lub biblioteki statyczne  
  
1.  Odwołanie do pliku odpowiedni nagłówek w kodzie za pomocą # dyrektywy include. Plik nagłówka musi być częścią bieżącego projektu lub ścieżkę include. Aby uzyskać więcej informacji, zobacz [#include — dyrektywa (C/C++)](../preprocessor/hash-include-directive-c-cpp.md).  
  
2.  Można również ustawić zależności projektu. Ustawienie zależności projektu gwarantuje dwie czynności. Najpierw gwarantuje, że projekty zostały skompilowane w odpowiedniej kolejności, tak aby projekt zawsze można znaleźć plików zależnych, których potrzebuje. Po drugie niejawnie dodaje katalog wyjściowy projektu zależnych na ścieżkę tak, aby pliki znajdują się łatwo w czasie konsolidacji.  
  
3.  Aby wdrożyć aplikację, należy umieścić biblioteki DLL w odpowiednim miejscu. Może to być jeden z następujących czynności:  
  
    1.  Taką samą ścieżkę pliku wykonywalnego.  
  
    2.  W dowolnym miejscu w ścieżce systemowej ( **ścieżki** zmienną środowiskową).  
  
    3.  W zestawie side-by-side. Aby uzyskać więcej informacji, zobacz [budynku C/C++--wspólny zestawy](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## <a name="working-with-multiple-projects"></a>Korzystanie z wielu projektów  
 Domyślnie projekty są tworzone w taki sposób, że wszystkie pliki wyjściowe są tworzone w podkatalogu w katalogu projektu. Katalog o nazwie na podstawie konfiguracji kompilacji (np. debugowanie lub wersji). Aby element równorzędny projekty do odwoływania się do siebie każdy projekt należy jawnie dodać innych katalogów wyjściowych projektu do ich ścieżki, aby połączenie powiodło się. Odbywa się to automatycznie po ustawieniu zależności projektu. Jednak jeśli nie używasz zależności, należy starannie samodzielnie to ponieważ kompilacji może stać się bardzo trudne do zarządzania. Na przykład gdy projekt ma konfiguracje Debug i Release i składa się z tego samego poziomu projektu biblioteki zewnętrznej, należy użyć pliku biblioteki różne w zależności od tego, którego konfiguracja została skompilowana. W związku z tym kodować tych ścieżek mogą być istotne znaczenie.  
  
 Wszystkie pliki niezbędne dane wyjściowe (takie jak pliki wykonywalne, pliki konsolidatora przyrostowego i pliki PDB) są kopiowane do wspólnego katalogu rozwiązania. W związku z tym podczas pracy z rozwiązaniem, które zawiera wiele projektów C++ z równoważną konfiguracji, wszystkie pliki wyjściowe są scentralizowane uproszczony konsolidacji i wdrażania. Można mieć pewność, że aplikacja/biblioteki będzie działać zgodnie z oczekiwaniami, jeśli ich Zachowaj tych plików (ponieważ pliki są gwarancji w ścieżce).  
  
 Lokalizacja plików wyjściowych można głównych problem w przypadku wdrażania w środowisku produkcyjnym. Podczas uruchamiania projektów w środowisku IDE, ścieżki do biblioteki dołączony niekoniecznie takie same jak w środowisku produkcyjnym. Na przykład, jeśli masz `#using "../../lib/debug/mylib.dll"` w kodzie, ale następnie wdrożyć mylib.dll do różnych pozycji względnej, aplikacja zakończy się niepowodzeniem w czasie wykonywania. Aby tego uniknąć, należy unikać używania ścieżek względnych w # instrukcji include w kodzie. Zaleca się upewnij się, że niezbędne pliki znajdują się w ścieżce kompilacji projektu i podobnie zapewnienie prawidłowo umieszczanie odpowiadające im pliki produkcji.  
  
#### <a name="how-to-specify-where-output-files-go"></a>Jak określić, gdzie Przejdź pliki wyjściowe  
  
1.  Lokalizacja projektu output ustawienia można znaleźć w projekcie **strony właściwości**. Rozwiń węzeł obok **właściwości konfiguracji** i wybierz **ogólne**. Lokalizacja danych wyjściowych określono obok **katalog wyjściowy**. Aby uzyskać więcej informacji, zobacz [ogólna strona właściwości (projekt)](../ide/general-property-page-project.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy projektów Visual C++](../ide/visual-cpp-project-types.md)