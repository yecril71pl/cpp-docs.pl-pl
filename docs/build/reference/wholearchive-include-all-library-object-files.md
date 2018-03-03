---
title: "-WHOLEARCHIVE (Dołącz wszystkie pliki obiekt bibliotece) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3499d6583c7d9801aa4c3b12c66196c975b192ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="wholearchive-include-all-library-object-files"></a>/ WHOLEARCHIVE (Dołącz wszystkie pliki obiekt bibliotece)
Wymuś na konsolidatorze załączenie wszystkich plików obiektów w bibliotece statycznej w połączonego pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
> / WHOLEARCHIVE [:*biblioteki*]  
  
## <a name="remarks"></a>Uwagi  
  
Opcja /WHOLEARCHIVE wymusza konsolidator, aby uwzględnić każdy plik obiektu z dowolnej określonej biblioteki statycznej, lub jeśli biblioteka nie jest określona, wszystkie biblioteki statyczne określone łącze polecenia z. Aby określić opcję /WHOLEARCHIVE wiele bibliotek, korzystając więcej niż jednego przełącznika /WHOLEARCHIVE w wierszu polecenia konsolidatora. Domyślnie konsolidator obejmuje plików obiektów w połączonych danych wyjściowych tylko wtedy, gdy ich eksportować symbole odwołuje się innych plików obiektów w pliku wykonywalnego. Opcja /WHOLEARCHIVE sprawia, że konsolidator Traktuj wszystkie pliki obiektu zarchiwizowane w bibliotece statycznej tak, jakby były indywidualnie określona w wierszu polecenia konsolidatora.  
  
Opcja /WHOLEARCHIVE można wyeksportować wszystkie symbole z biblioteką statyczną. Dzięki temu można upewnij się, że wszystkie kod biblioteki, zasobów i metadane są uwzględniane podczas tworzenia składnika z więcej niż jednej biblioteki statycznej. Jeśli zostanie wyświetlone ostrzeżenie LNK4264 podczas tworzenia biblioteki statycznej zawiera składniki środowiska uruchomieniowego systemu Windows eksportu, należy użyć opcji /WHOLEARCHIVE podczas konsolidacji tej biblioteki do innego składnika lub aplikacji.  
  
Opcja /WHOLEARCHIVE została wprowadzona w programie Visual Studio 2015 Update 2.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
1.  Wybierz **wiersza polecenia** strony właściwości w obszarze **właściwości konfiguracji**, **konsolidatora**.  
  
1.  Dodaj opcję /WHOLEARCHIVE **dodatkowe opcje** pola tekstowego.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)