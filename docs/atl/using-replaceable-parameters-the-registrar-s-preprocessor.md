---
title: Używanie wymiennych parametrów (Rejestrator ALT) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- AddReplacement
- ClearReplacements
dev_langs:
- C++
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eddeb6467dfb3bf578c0287161de989e8ba12483
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097474"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Używanie wymiennych parametrów (Rejestrator&#39;preprocesora s)

Parametry wymienne pozwalają rejestratora klientów określić dane czasu wykonywania. Aby to zrobić, Rejestrator przechowuje mapy zastąpienia, w którym wchodzi wartości skojarzone z parametry zmienne w skrypcie. Rejestrator sprawia, że te wpisy w czasie wykonywania.

##  <a name="_atl_using_.25.module.25"></a> Przy użyciu modułu %

[Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md) automatycznie generuje skrypt, który używa `%MODULE%`. ATL używa ten parametr do zastąpienia dla rzeczywistej lokalizacji danych na serwerze biblioteki DLL lub EXE.

## <a name="concatenating-run-time-data-with-script-data"></a>Łączenie danych czasu wykonywania przy użyciu danych ze skryptów

Innym zastosowaniem preprocesora jest łączenie danych czasu wykonywania przy użyciu danych skryptu. Załóżmy, że wpis jest potrzebny zawierającą pełną ścieżkę do modułu z ciągiem "`, 1`" dołączany na końcu. Najpierw należy zdefiniować następujące rozszerzenia:

```
'MySampleKey' = s '%MODULE%, 1'
```

Następnie przed wywołaniem skryptu przetwarzania metody wymienionej w [wywoływanie skryptów](../atl/invoking-scripts.md), dodać zamiennika do mapy:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Podczas analizowania skryptu rejestratora rozwija `'%MODULE%, 1'` do `c:\mycode\mydll.dll, 1`.

> [!NOTE]
>  W przypadku skryptu rejestratora 4K jest maksymalny rozmiar tokenu. (Token jest dowolny element rozpoznawalną w składni). Dotyczy to również tokenów, które zostały utworzone lub rozszerzać przez preprocesor.

> [!NOTE]
>  Aby zastąpić wartości zastępcze w czasie wykonywania, Usuń wywołanie funkcji w skrypcie [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) makra. Zamiast tego należy zastąpić własnymi `UpdateRegistry` metodę, która wywołuje [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)i przekazać macierz _ATL_REGMAP_ Struktury wpisu. Macierz _ATL_REGMAP_ENTRY musi mieć co najmniej jeden wpis, który jest ustawiony na {wartość NULL, NULL}, a ten wpis powinien zawsze być ostatni wpis. W przeciwnym razie błąd naruszenia zasad dostępu będzie generowany, jeśli `UpdateRegistryFromResource` jest wywoływana.

> [!NOTE]
>  Podczas kompilowania projektu, który generuje plik wykonywalny, ATL automatycznie dodaje znaki cudzysłowu otaczające tworzony w czasie wykonywania za pomocą nazwy ścieżki **modułu %** parametru skryptu rejestratora. Jeśli chcesz, aby nazwę ścieżki aby używać znaków cudzysłowu, użyj nowego **MODULE_RAW %** parametru zamiast tego.
>
>  Podczas kompilowania projektu, który wyprowadza biblioteki DLL, ATL nie doda znaków cudzysłowu do nazwy ścieżki Jeśli **modułu %** lub **MODULE_RAW %** jest używany.

## <a name="see-also"></a>Zobacz też

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)

