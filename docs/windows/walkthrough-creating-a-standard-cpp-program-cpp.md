---
title: 'Wskazówki: Tworzenie standardowego programu C++ (C++) | Dokumentacja firmy Microsoft'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vcfirstapp
- vccreatefirst
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], standard
- standard applications [C++]
ms.assetid: 48217e35-d892-46b7-93e3-f6f0b7e2da35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac1fac3c7f96c9f8d718efa54810f4155b1ddac5
ms.sourcegitcommit: c0ffdff538eb961f786809eb547b35846190ee48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2018
ms.locfileid: "34800089"
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
  
2.  W **Visual C++** okienko typy projektu, kliknij przycisk **Windows Desktop**, a następnie kliknij przycisk **aplikacji konsoli systemu Windows**.  
  
3.  Wpisz nazwę dla projektu.  
  
     Domyślnie rozwiązanie, które zawiera projekt ma taką samą nazwę jak projekt, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.  
  
     Kliknij przycisk **OK** Aby utworzyć projekt.  
  
4.  Jeśli **Eksploratora rozwiązań** nie jest wyświetlany na **widoku** menu, kliknij przycisk **Eksploratora rozwiązań**.  
  
5.  Dodaj nowy plik źródłowy do projektu, w następujący sposób.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pliki źródłowe** folderu, wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
    2.  W **kod** węzła, kliknij przycisk **plik C++ (.cpp)**, wpisz nazwę pliku, a następnie kliknij przycisk **Dodaj**.  
  
     Plik .cpp pojawia się w folderze plików źródłowych w **Eksploratora rozwiązań**, a plik jest otwarty w edytorze programu Visual Studio.  
  
6.  W pliku w edytorze wpisz prawidłowy program w języku C++, który używa standardowa biblioteka C++ lub skopiować jeden przykładowe programy i wklej go w pliku.  
  
7.  Zapisz plik.  
  
8. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     **Dane wyjściowe** okno wyświetla informacje o postępie kompilacji, na przykład lokalizację dziennika kompilacji i komunikat, który wskazuje stan kompilacji.  
  
9. Na **debugowania** menu, kliknij przycisk **uruchomić bez debugowania**.  
  
     Jeśli użyto przykładowy program okno polecenia zostanie wyświetlony i pokazuje, czy niektóre liczb całkowitych znajdują się w zestawie.  
  
## <a name="next-steps"></a>Następne kroki  
 **Poprzedni:** [konsoli aplikacji w programie Visual C++](../windows/console-applications-in-visual-cpp.md). **Następnie:**[wskazówki: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)
