---
title: "Składnia wiersza polecenia konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ce42aa031b91d5a4ec21ed14ac7cb47643e1325
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-command-line-syntax"></a>Składnia wiersza polecenia konsolidatora
Aby uruchomić łącza. EXE, należy użyć następującej składni polecenia:  
  
```  
LINK arguments  
```  
  
 `arguments` Obejmują opcje i nazwy plików i może zostać określony w dowolnej kolejności. Opcje są przetworzonych pierwszy, a następnie plików. Użyj spacji lub karty do oddzielania argumentów.  
  
> [!NOTE]
>  Można uruchomić to narzędzie tylko z [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] wiersza polecenia. Nie można uruchomić go z wiersza polecenia systemu lub z Eksploratora plików.  
  
 W wierszu polecenia opcję składa się z specyfikator opcji kreski (-) i ukośnika (/), a następnie Nazwa opcji. Nie można stosować skrót nazw opcji. Niektóre opcje przyjmuje argumentu, podać po dwukropkiem (:). Bez spacji i karty są dozwolone w obrębie Specyfikacja opcji z wyjątkiem ciągu ujętego w cudzysłów w opcji/Comment. Określ argumenty liczbowe w wartości dziesiętne lub notacji języka C. Opcja nazwy i ich argumentów — słowo kluczowe lub nazwa pliku nie jest uwzględniana, ale identyfikatory jako argumentów jest rozróżniana wielkość liter.  
  
 Aby przekazać plik do konsolidatora, określ nazwę pliku w wierszu polecenia po poleceniu łącza. Można podać ścieżką bezwzględną ani względną nazwę pliku, a w nazwie pliku można używać symboli wieloznacznych. W przypadku pominięcia kropkę (.) i rozszerzenie nazwy pliku, LINK zakłada .obj w celu znajdowania plików. ŁĄCZE nie umożliwia rozszerzenia nazwy pliku lub brak ich zakładają zawartość plików. Określa typ pliku, sprawdzając go i odpowiednio je przetwarza.  
  
 Link.exe zwraca zero w przypadku powodzenia (bez błędów).  W przeciwnym razie konsolidator zwraca kod błędu zatrzymania łącza.  Na przykład jeśli konsolidator wygeneruje LNK1104, konsolidator zwraca 1104.  W związku z tym najniższy numer błędu zwrócony w przypadku wystąpienia błędu przez konsolidator wynosi 1000.  Zwracana wartość 128 reprezentuje problem z konfiguracją systemu operacyjnego lub pliku .config; Moduł ładujący nie został załadowany link.exe lub c2.dll.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)