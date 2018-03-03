---
title: "-MANIFESTINPUT (Określ dane wejściowe manifestu) | Dokumentacja firmy Microsoft"
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
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1eec78675845e3f738bb0b6b440b3a71f1fd572
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (Określ dane wejściowe manifestu)
Określa plik wejściowy manifestu do uwzględnienia w manifeście, dla których jest osadzony w obrazie.  
  
## <a name="syntax"></a>Składnia  
  
```  
/MANIFESTINPUT:filename  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Plik manifestu do uwzględnienia w manifeście osadzonych.  
  
## <a name="remarks"></a>Uwagi  
 **/MANIFESTINPUT** opcji określa ścieżkę pliku wejściowego używać do tworzenia manifestu osadzonego obrazu wykonywalnego. Jeśli masz wiele manifest pliki wejściowe, użyj przełącznika wiele razy — raz dla każdego pliku wejściowego. Pliki wejściowe manifestu zostaną scalone tworzenie manifestu osadzonych. Ta opcja wymaga **/MANIFEST: OSADZANIE** opcji.  
  
 Ta opcja nie można ustawić bezpośrednio w [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]. Zamiast tego należy użyć **dodatkowe pliki manifestu** właściwości projektu, aby określić dodatkowe pliki manifestu do uwzględnienia. Aby uzyskać więcej informacji, zobacz [danych wejściowych i wyjściowych, narzędziu manifestu, właściwości konfiguracji \<Projectname > strony właściwości — okno dialogowe](../../ide/input-and-output-manifest-tool.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)   
 [Opcje konsolidatora](../../build/reference/linker-options.md)