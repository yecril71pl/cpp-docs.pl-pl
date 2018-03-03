---
title: "Przy użyciu parametry wymienne (Rejestrator ALT) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AddReplacement
- ClearReplacements
dev_langs:
- C++
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b06333ba51b74501f3b7cd68248e5fb7e51ca94f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Przy użyciu parametry wymienne (rejestratora &#39; preprocesora s)
Parametry wymienne Zezwalaj klientowi rejestratora Określ dane czasu wykonywania. Aby to zrobić, rejestratora obsługuje mapy zastąpienia, w której wchodzi wartości skojarzone z parametry zmienne w skrypcie. Rejestratora sprawia, że te wpisy w czasie wykonywania.  
  
##  <a name="_atl_using_.25.module.25"></a>Przy użyciu modułu %  
 [Kreator formantu ATL](../atl/reference/atl-control-wizard.md) automatycznie generuje skryptu, który używa `%MODULE%`. ATL używa tego parametru replaceable rzeczywistej lokalizacji na serwerze biblioteki DLL lub EXE.  
  
## <a name="concatenating-run-time-data-with-script-data"></a>Łączenie danych czasu wykonywania z danymi skryptu  
 Użycie innego preprocesora jest łączenie danych czasu wykonywania z danych skryptu. Na przykład, załóżmy, że wpis jest potrzebna, który zawiera pełną ścieżkę do modułu z ciągiem "`, 1`" dołączany na końcu. Najpierw należy zdefiniować następujące rozszerzenia:  
  
```  
'MySampleKey' = s '%MODULE%, 1'  
```  
  
 Następnie przed wywołaniem metody na liście przetwarzania skryptu [skrypty wywołania](../atl/invoking-scripts.md), dodać zastępczy do mapy:  
  
 [!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]  
  
 Podczas analizowania skryptu rejestratora rozszerza `'%MODULE%, 1'` do `c:\mycode\mydll.dll, 1`.  
  
> [!NOTE]
>  W przypadku skryptu rejestratora 4K jest maksymalny rozmiar tokenu. (Token jest dowolny element rozpoznawalną w składni). W tym tokenów, które zostały utworzone lub rozszerzać przez preprocesora.  
  
> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, Usuń wywołanie w skrypcie [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) makra. Zamiast tego należy zastąpić własnymi `UpdateRegistry` — metoda, która wywołuje [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)i przekaż z tablicy **_ATL_REGMAP_ENTRY** struktury. Tablica z **_ATL_REGMAP_ENTRY** musi mieć co najmniej jeden wpis, który ma ustawioną wartość {**NULL**,**NULL**}, ten wpis należy zawsze ostatniego zapisu. W przeciwnym razie błąd naruszenia zasad dostępu będzie generowane, gdy **UpdateRegistryFromResource** jest wywoływana.  
  
> [!NOTE]
>  Podczas kompilowania projektu, który generuje plik wykonywalny, ATL automatycznie dodaje nazwę ścieżki tworzone w czasie wykonywania w języku w cudzysłowie **modułu %** parametr skryptu rejestratora. Jeśli nie chcesz, aby nazwa ścieżki do znaków cudzysłowu, użyj nowych **MODULE_RAW %** parametru zamiast tego.  
>   
>  Podczas kompilowania projektu, który wyprowadza biblioteki DLL, ATL nie doda znaków cudzysłowu do nazwy ścieżki Jeśli **modułu %** lub **MODULE_RAW %** jest używany.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)

