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
ms.openlocfilehash: 0915f6f506b942a7ee52eec637c9ea6631339e79
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643286"
---
# <a name="walkthrough-creating-a-standard-c-program-c"></a>Wskazówki: Tworzenie standardowego programu C++ (C++)
Aby tworzyć programy standardowego C++, można użyć Visual C++ w programie Visual Studio zintegrowane środowisko programistyczne (IDE). Wykonując kroki opisane w tym instruktażu, można utworzyć projekt, Dodaj nowy plik do projektu, zmodyfikuj plik, aby dodać kod języka C++, a następnie skompilować i uruchomić program za pomocą [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
 Można wpisać swój własny program C++ lub użyć jednego z przykładowych programów. Przykładowy program w tym instruktażu jest aplikacją konsoli. Ta aplikacja używa `set` kontenera w standardowej biblioteki języka C++.  
  
 Visual C++, który jest zgodny ze standardem C++ 2003, z tymi wyjątkami: dwuetapowego odnośnik do nazwy, specyfikacja wyjątku i eksport. Ponadto Visual C++ obsługuje kilka C ++ 0 x funkcji, na przykład wyrażenia lambda, auto, static_assert, odwołania rvalue i szablony extern.  
  
> [!NOTE]
>  Jeśli wymagana jest zgodność ze standardem, użyj `/Za` opcję kompilatora, aby wyłączyć rozszerzenia Microsoft do standardu. Aby uzyskać więcej informacji, zobacz [/za, /Ze (Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten instruktaż, musisz rozumieć podstawy języka C++.  
  
### <a name="to-create-a-project-and-add-a-source-file"></a>Aby utworzyć projekt i dodać plik źródłowy  
  
1.  Utwórz projektu wskazując **New** na **pliku** menu, a następnie klikając polecenie **projektu**.  
  
2.  W **Visual C++** okienku typów projektu, kliknij przycisk **pulpitu Windows**, a następnie kliknij przycisk **aplikacji konsoli Windows**.  
  
3.  Wpisz nazwę dla projektu.  
  
     Domyślnie rozwiązanie, zawierający projekt ma taką samą nazwę jak projektu, ale można wpisać inną nazwę. Możesz również wpisać inną lokalizację dla projektu.  
  
     Kliknij przycisk **OK** do tworzenia projektu.  
  
4.  Jeśli **Eksploratora rozwiązań** nie jest wyświetlany na **widoku** menu, kliknij przycisk **Eksploratora rozwiązań**.  
  
5.  Dodaj nowy plik źródłowy do projektu, w następujący sposób.  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pliki źródłowe** folderu, wskaż **Dodaj**, a następnie kliknij przycisk **nowy element**.  
  
    2.  W **kodu** węzła, kliknij przycisk **plik C++ (.cpp)**, wpisz nazwę pliku, a następnie kliknij **Dodaj**.  
  
     Plik CPP pojawia się w folderze plików źródłowych w **Solution Explorer**, a plik jest otwarty w edytorze programu Visual Studio.  
  
6.  W pliku w edytorze wpisz prawidłowy program w języku C++, który używa standardowej biblioteki C++ lub skopiuj jeden z przykładowych programów i wklej go w pliku.  
  
7.  Zapisz plik.  
  
8. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     **Dane wyjściowe** okna wyświetla informacje o postępie kompilacji, na przykład lokalizacja dziennika kompilacji i komunikat o statusie kompilacji.  
  
9. Na **debugowania** menu, kliknij przycisk **Uruchom bez debugowania**.  
  
     Jeśli użyto przykładowego programu, okno polecenia jest wyświetlane i pokazuje, czy niektóre liczby całkowite znajdują się w zestawie.  
  
## <a name="next-steps"></a>Następne kroki  
 **Poprzedni:** [konsoli aplikacji w języku Visual C++](../windows/console-applications-in-visual-cpp.md). **Następnie:**[wskazówki: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)