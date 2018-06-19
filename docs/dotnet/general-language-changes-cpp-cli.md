---
title: Ogólne zmiany w języku (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: aede6cc0d4bd8e50d8662f301ffdfb7b6179a230
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109141"
---
# <a name="general-language-changes-ccli"></a>Ogólne zmiany w języku (C++/CLI)
Liczba — funkcje językowe CLR zmieniła się z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Zmiany opisane w tej sekcji są sortowania miscellany języka. Obejmuje zmiany w obsłudze literałów ciągu, zmiana wiązaniem między wielokropek i `Param` atrybutów, zmiany `typeof` do `typeid`, zmiany w wywołaniu elementu listy inicjatorów konstruktora i wprowadzenie nowej notacji rzutowania z `safe_cast`.  
  
 [Literał ciągu](../dotnet/string-literal.md)  
 W tym artykule omówiono sposób obsługi literałów ciągów została zmieniona.  
  
 [Tablica parametrów i wielokropek](../dotnet/param-array-and-ellipsis.md)  
 W tym artykule omówiono sposób `ParamArray` jest teraz pierwszeństwo nad wielokropka (`...`) w celu rozwiązania wywołania funkcji z różną liczbę argumentów.  
  
 [Operator typeof został zastąpiony operatorem T::typeid](../dotnet/typeof-goes-to-t-typeid.md)  
 W tym artykule omówiono sposób `typeof` operator ma zostać supplanted przez `typeid`.  
  
 [Listy inicjatorów](../dotnet/initializer-lists.md)  
 Zawiera omówienie zmian w kolejności wywoływania listy inicjatorów.  
  
 [Notacja rzutowania i przedstawienie operacji safe_cast<>](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)  
 Zawiera omówienie zmian do notacji rzutowania, w szczególności wprowadzenia `safe_cast`.  
  
## <a name="see-also"></a>Zobacz też  
 [Podręcznik migracji C++/CLI](../dotnet/cpp-cli-migration-primer.md)