---
title: 'Porady: tworzenie weryfikowalnych projektów C++ (C + +/ CLI) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a012e52a8eb825c3ffc6b694c888cef8a174f37e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>Porady: tworzenie weryfikowalnych projektów C++ (C++/CLI)
Kreatorzy aplikacji w usłudze Visual C++ nie twórz weryfikowalnych projektów, ale projekty mogą być konwertowane jako możliwe do zweryfikowania. W tym temacie opisano sposób ustawiania właściwości projektu i zmodyfikować pliki źródłowe projektu do przekształcania projektów Visual C++ do tworzenia aplikacji możliwe do zweryfikowania.  
  
## <a name="compiler-and-linker-settings"></a>Kompilator i ustawienia konsolidatora  
 Domyślnie projektów .NET Użyj flagi kompilator/CLR i skonfigurować konsolidator, aby docelowy x86 sprzętu. W przypadku weryfikowalny kod należy użyć flagi/CLR: Safe i należy poinstruować konsolidator, aby wygenerować MSIL zamiast instrukcji natywny maszyny.  
  
#### <a name="to-change-the-compiler-and-linker-settings"></a>Aby zmienić ustawienia kompilatorze i konsolidatorze  
  
1.  Wyświetl stronę właściwości projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
2.  Na **ogólne** w obszarze **właściwości konfiguracji** zestaw węzłów, **Obsługa środowiska uruchomieniowego CLR** właściwości **bezpieczne wspólnego języka MSIL Obsługa środowiska uruchomieniowego (/ CLR: Safe)**.  
  
3.  Na **zaawansowane** w obszarze **konsolidatora** zestaw węzłów, **typu obrazu CLR** właściwości **Wymuś bezpieczny obraz IL (/ clrimagetype: Safe)**.  
  
## <a name="removing-native-data-types"></a>Usuwanie danych natywnych typów  
 Ponieważ macierzyste typy danych z systemem innym niż — możliwe do zweryfikowania, nawet jeśli nie są rzeczywiście używane, należy usunąć wszystkie pliki nagłówka zawierające natywnych typów.  
  
> [!NOTE]
>  Poniższa procedura ma zastosowanie do projektów aplikacji formularzy systemu Windows (.NET) i konsoli aplikacji (.NET).  
  
#### <a name="to-remove-references-to-native-data-types"></a>Aby usunąć odwołania do typów danych w trybie macierzystym  
  
1.  Komentarz wszystko w pliku Stdafx.h.  
  
## <a name="configuring-an-entry-point"></a>Konfigurowanie punktu wejścia  
 Ponieważ weryfikowalny aplikacje nie mogą używać biblioteki wykonawcze języka C (CRT), nie mogą być zależne na CRT w wywołaniu funkcji main jako punkt wejścia standardowego. Oznacza to, że jawnie Podaj nazwę funkcji do wywołania początkowo konsolidator. (W tym przypadku Main() jest używany zamiast main() lub _tmain(), aby wskazać punkt wejścia nie CRT, ale ponieważ punkt wejścia musi zostać określone jawnie, ta nazwa jest dowolne).  
  
> [!NOTE]
>  Poniższe procedury dotyczą projekty konsoli aplikacji (.NET).  
  
#### <a name="to-configure-an-entry-point"></a>Aby skonfigurować punkt wejścia  
  
1.  Zmień _tmain() Main() w pliku .cpp głównym projektu.  
  
2.  Wyświetl stronę właściwości projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
3.  Na **zaawansowane** w obszarze **konsolidatora** węzła, wprowadź `Main` jako **punktu wejścia** wartości właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Kod czysty i weryfikowalny (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)