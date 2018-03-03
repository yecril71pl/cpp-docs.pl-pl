---
title: "Wskazówki: Tworzenie standardowego programu C++ (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vcfirstapp
- vccreatefirst
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 52066be1d67bddb7173841e9df6c5013c86ac0dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Wskazówki: Tworzenie standardowego programu C++ (C++)
Visual C++ w programie Visual Studio zintegrowane środowisko programistyczne (IDE) służy do tworzenia programy Standard C++. Wykonując kroki opisane w tym przewodniku, można utworzyć projekt, Dodaj nowy plik do projektu, zmodyfikuj plik, aby dodać kod w języku C++, a następnie skompilować i uruchomić program przy użyciu [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 Można wpisać programu C++ lub użyj jednego z programów przykładowych. Przykładowy program w tym przewodniku jest aplikacji konsoli. Ta aplikacja używa `set` kontenera w standardowej bibliotece C++.  
  
 Visual C++ jest zgodny z 2003 Standard C++, z następującymi wyjątkami głównych: wyszukiwanie nazw dwuetapowa, specyfikacje wyjątków i eksportowanie. Ponadto Visual C++ obsługuje kilka funkcji C ++ 0 x, na przykład wyrażenia lambda, automatycznie static_assert, odwołania do r-wartości i szablonów zewnętrzny.  
  
> [!NOTE]
>  Jeśli wymagana jest zgodności ze standardem, użyj **/Za** opcję kompilatora, aby wyłączyć rozszerzenia Microsoft do standardowego. Aby uzyskać więcej informacji, zobacz [/Za, /Ze (Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten instruktaż, musisz rozumieć podstawy języka C++.  
  
### <a name="to-create-a-project-and-add-a-source-file"></a>Aby utworzyć projekt i dodać pliku źródłowego  
  
1.  Utwórz projekt poprzez wskazanie **nowy** na **pliku** menu, a następnie klikając pozycję **projektu**.  
  
2.  W **Visual C++** okienko typy projektu, kliknij przycisk **Win32**, a następnie kliknij przycisk **aplikacji konsoli Win32**.  
  
3.  Wpisz nazwę dla projektu.  
  
     Domyślnie rozwiązanie, które zawiera projekt ma taką samą nazwę jak projekt, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.  
  
     Kliknij przycisk **OK** Aby utworzyć projekt.  
  
4.  W **Kreator aplikacji Win32**, kliknij przycisk **dalej**, wybierz pozycję **pusty projekt**, a następnie kliknij przycisk **Zakończ**.  
  
5.  Jeśli **Eksploratora rozwiązań** nie jest wyświetlany na **widoku** menu, kliknij przycisk **Eksploratora rozwiązań**.  
  
6.  Dodaj nowy plik źródłowy do projektu, w następujący sposób.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pliki źródłowe** folderu, wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
    2.  W **kod** węzła, kliknij przycisk **plik C++ (.cpp)**, wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.  
  
     Plik .cpp pojawia się w folderze plików źródłowych w **Eksploratora rozwiązań**, a plik jest otwarty w edytorze programu Visual Studio.  
  
7.  W pliku w edytorze wpisz prawidłowy program w języku C++, który używa standardowa biblioteka C++ lub skopiować jeden przykładowe programy i wklej go w pliku.  
  
8.  Zapisz plik.  
  
9. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     **Dane wyjściowe** okno wyświetla informacje o postępie kompilacji, na przykład lokalizację dziennika kompilacji i komunikat, który wskazuje stan kompilacji.  
  
10. Na **debugowania** menu, kliknij przycisk **uruchomić bez debugowania**.  
  
     Jeśli użyto przykładowy program okno polecenia zostanie wyświetlony i pokazuje, czy niektóre liczb całkowitych znajdują się w zestawie.  
  
## <a name="next-steps"></a>Następne kroki  
 **Poprzedni:** [konsoli aplikacji w programie Visual C++](../windows/console-applications-in-visual-cpp.md). **Następnie:**[wskazówki: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)