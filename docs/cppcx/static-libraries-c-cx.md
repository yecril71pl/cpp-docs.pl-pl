---
title: Biblioteki statyczne (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ffa905cbe0fd49489bd3634cb927cce57ea4ddbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="static-libraries-ccx"></a>Biblioteki statyczne (C + +/ CX)
Biblioteka statyczna, który jest używany w aplikacji Windows platformy Uniwersalnej mogą zawierać kod normy ISO C++, w tym typy STL i wywołania funkcji Win32 API, które nie są wykluczone z platformy aplikacji środowiska wykonawczego systemu Windows. Biblioteka statyczna zużywa składników środowiska wykonawczego systemu Windows i może utworzyć składników środowiska wykonawczego systemu Windows z pewnymi ograniczeniami.  
  
## <a name="creating-static-libraries"></a>Tworzenie biblioteki statyczne  
  
#### <a name="to-create-a-static-library-for-use-in-a-uwp-app"></a>Do tworzenia biblioteki statycznej do użycia w aplikacji platformy uniwersalnej systemu Windows  
  
1.  Na pasku menu wybierz **pliku** > **nowy** > **projektu**. W obszarze **Visual C++** > **uniwersalnych systemu Windows** wybierz **biblioteka statyczna (uniwersalna systemu Windows)**.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz pozycję **właściwości**. W **właściwości** na okna dialogowego **właściwości konfiguracji** > **C/C++** ustaw **korzystać rozszerzenie środowiska uruchomieniowego systemu Windows** do **tak (/ZW)**.  
  
 Podczas kompilowania nowej biblioteki statyczne, jeśli wywołanie interfejsu API Win32, które jest wyłączone dla aplikacji platformy uniwersalnej systemu Windows, kompilator zgłosi błąd C3861, "Nie odnaleziono identyfikatora". Aby wyszukać alternatywną metodą jest obsługiwana w przypadku środowiska uruchomieniowego systemu Windows, temacie [alternatywy dla interfejsów API systemu Windows w aplikacjach platformy uniwersalnej systemu Windows](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).  
  
 Po dodaniu projektu biblioteki statycznej C++ do rozwiązania aplikacji platformy uniwersalnej systemu Windows może być konieczne zaktualizowanie ustawień właściwości projektu biblioteki, tak aby właściwość pomocy technicznej platformy uniwersalnej systemu Windows jest ustawiona na **tak**. Bez tego ustawienia kompilacji kodu i linki, ale wystąpił błąd występuje, gdy użytkownik podejmie próbę sprawdzić, czy aplikacja Microsoft Store. Statycznej lib powinna być skompilowana z tymi samymi ustawieniami kompilatora jako projekt, który wykorzystuje go.  
  
 Jeśli korzystać bibliotekę statyczną, która tworzy publiczny `ref` klasy, klasy interfejs publiczny lub klasy wartość publicznego konsolidator zgłasza to ostrzeżenie:  
  
> **Ostrzeżenie LNK4264:** archiwizowanie pliku obiektu skompilowanego z parametrem /ZW do biblioteki statycznej; należy pamiętać, że podczas tworzenia typów środowiska wykonawczego systemu Windows nie zaleca się połączyć z biblioteką statyczną zawierającą metadane środowiska wykonawczego systemu Windows.  
  
 Można bezpiecznie zignorować to ostrzeżenie, tylko wtedy, gdy biblioteka statyczna nie wytwarza składników środowiska wykonawczego systemu Windows, które są używane poza samej biblioteki. Jeśli biblioteka nie korzystać składnik, który definiuje, następnie konsolidator zoptymalizować optymalizacji wdrożenia nawet publicznego metadane zawierają informacje o typie. Oznacza to, że składniki publicznego w bibliotece statycznej zostanie skompilowany, ale nie będą aktywowane w czasie wykonywania. Z tego powodu jakikolwiek składnik środowiska wykonawczego systemu Windows jest przeznaczony do użytku przez inne składniki lub aplikacji musi być implementowana w biblioteki dołączanej (dynamicznie DLL).  
  
## <a name="see-also"></a>Zobacz też  
 [Wątkowość i organizowanie](../cppcx/threading-and-marshaling-c-cx.md)