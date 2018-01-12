---
title: Szablon projektu biblioteki klas WRL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
ms.assetid: 628b0852-89e5-44f8-bf58-a09762bda15c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 13fc476f696bdd2cb17ed58c496c63747db90322
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="wrl-class-library-project-template"></a>Szablon projektu biblioteki klas WRL
Zapisywanie projektu Windows środowiska uruchomieniowego C++ szablonu biblioteki (WRL) za pomocą programu Visual Studio może bardzo uprościć zadania pobierając szablon projektu biblioteki klas WRL.  
  
> [!NOTE]
>  Jeśli musisz ręcznie zaktualizować ustawienia projektu dla istniejącego projektu, zobacz [biblioteki dll (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh699881\(v=vs.110\).aspx).  
  
## <a name="download-the-wrl-project-template"></a>Pobierz szablon projektu biblioteki WRL  
 Program Visual Studio nie zapewnia szablonu dla projektów Biblioteka szablonów C++ środowiska wykonawczego systemu Windows. Poniżej przedstawiono sposób pobrać szablonu projektu, który tworzy bibliotekę klasa podstawowa dla aplikacji platformy uniwersalnej systemu Windows z Biblioteka szablonów C++ środowiska wykonawczego systemu Windows.  
  
#### <a name="to-download-the-wrl-project-template"></a>Aby pobrać szablon projektu biblioteki WRL  
  
1.  Na pasku menu wybierz **pliku**, **nowy projekt**.  
  
2.  W lewym okienku **nowy projekt** okno dialogowe, wybierz opcję **Online**, a następnie wybierz **szablony**.  
  
3.  W **wyszukiwania szablonów online** polu w prawym górnym rogu, typ `WRL Class Library`. Jeśli szablon zostanie wyświetlony w wynikach wyszukiwania, wybierz **OK** przycisku.  
  
4.  W **Pobierz i zainstaluj** warunki okno dialogowe, jeśli akceptujesz licencji, wybierz **zainstalować** przycisku.  
  
5.  Po zainstalowaniu szablonu, utworzyć projekt, wybierając **pliku**, **nowy projekt**, a następnie wybierając `WRLClassLibrary` szablonu. Projekt tworzy bibliotekę DLL.  
  
## <a name="examples-that-use-the-project-template"></a>Przykłady, których należy użyć szablonu projektu  
 Odczyt [wskazówki: Tworzenie podstawowego składnika środowiska wykonawczego systemu Windows](../windows/walkthrough-creating-a-basic-windows-runtime-component-using-wrl.md) na przykład używające tego szablonu do tworzenia składnika środowiska wykonawczego systemu Windows.  
  
## <a name="what-the-project-template-provides"></a>Szablon projektu zawiera  
 Szablon projektu zawiera:  
  
-   pliku .idl, który deklaruje atrybuty MIDL podstawowy interfejs jej Implementacja klasy. Oto przykład.  
  
     [!code-cpp[wrl-project-template#1](../windows/codesnippet/CPP/wrl-class-library-project-template_1.idl)]  
  
-   plik .cpp, który definiuje implementację klasy. Oto przykład.  
  
     [!code-cpp[wrl-project-template#2](../windows/codesnippet/CPP/wrl-class-library-project-template_2.cpp)]  
  
     [Runtimeclass —](../windows/runtimeclass-class.md) klasy podstawowej ułatwia zarządzanie odwołanie globalne do wszystkich obiektów w module i deklaruje metody [IUnknown](http://msdn.microsoft.com/en-us/33f1d79a-33fc-4ce5-a372-e08bda378332) i [IInspectable](http://msdn.microsoft.com/en-us/0657e51f-d4c0-46c6-927d-b01e54b6846c) interfejsów. [Inspectableclass —](../windows/inspectableclass-macro.md) implementuje makro `IUnknown` i `IInspectable`. [ActivatableClass](../windows/activatableclass-macros.md) makro tworzy fabrykę klas, która tworzy wystąpienia klasy.  
  
-   plik o nazwie module.cpp, który definiuje biblioteki eksportuje `DllMain`, `DllCanUnloadNow`, `DllGetActivationFactory`, i `DllGetClassObject`.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)