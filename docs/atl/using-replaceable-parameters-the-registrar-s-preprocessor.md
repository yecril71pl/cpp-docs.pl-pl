---
title: Używanie wymiennych parametrów (rejestrator ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 2474db2de384baa9113ed39aef4d3d9c9048903d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329228"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Korzystanie z parametrów wymiennych (rejestrator&#39;s Preprocessor)

Wymienne parametry umożliwiają klientowi rejestratora określenie danych w czasie wykonywania. W tym celu rejestrator zachowuje mapę zastępczą, do której wprowadza wartości skojarzone z wymiennymi parametrami w skrypcie. Rejestrator wprowadza te wpisy w czasie wykonywania.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>Korzystanie z %MODULE%

[Kreator sterowania ATL](../atl/reference/atl-control-wizard.md) automatycznie generuje skrypt, `%MODULE%`który używa . ATL używa tego wymiennego parametru dla rzeczywistej lokalizacji biblioteki DLL lub EXE serwera.

## <a name="concatenating-run-time-data-with-script-data"></a>Łączenie danych w czasie wykonywania z danymi skryptu

Innym zastosowaniem preprocesora jest łączenie danych w czasie wykonywania z danymi skryptu. Załóżmy na przykład, że potrzebny jest wpis zawierający`, 1`pełną ścieżkę do modułu z ciągiem " " " dołączonym na końcu. Najpierw zdefiniuj następujące rozszerzenie:

```
'MySampleKey' = s '%MODULE%, 1'
```

Następnie przed wywołaniem jednej z metod przetwarzania skryptów wymienionych w [wywoływaniu skryptów](../atl/invoking-scripts.md)dodaj zamiennik do mapy:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Podczas analizowania skryptu rejestrator rozszerza `'%MODULE%, 1'` się do `c:\mycode\mydll.dll, 1`.

> [!NOTE]
> W skrypcie rejestratora 4K jest maksymalny rozmiar tokenu. (Token jest dowolnym rozpoznawalnym elementem w składni.) Obejmuje to tokeny, które zostały utworzone lub rozwinięte przez preprocesora.

> [!NOTE]
> Aby zastąpić wartości zastępcze w czasie wykonywania, usuń wywołanie w skrypcie do [makra DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) lub [DECLARE_REGISTRY_RESOURCEID.](../atl/reference/registry-macros.md#declare_registry_resourceid) Zamiast tego zastąp `UpdateRegistry` go własną metodą, która wywołuje [CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) lub [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)i przekaż tablicę struktur _ATL_REGMAP_ENTRY. Tablica _ATL_REGMAP_ENTRY musi mieć co najmniej jeden wpis ustawiony na {NULL,NULL}, a ten wpis powinien być zawsze ostatnim wpisem. W przeciwnym razie błąd naruszenia `UpdateRegistryFromResource` zasad dostępu zostanie wygenerowany, gdy zostanie wywołany.

> [!NOTE]
> Podczas tworzenia projektu, który wyprowadza plik wykonywalny, ATL automatycznie dodaje znaki cudzysłowu wokół nazwy ścieżki utworzonej w czasie wykonywania z parametrem skryptu **rejestratora %MODULE%.** Jeśli nazwa ścieżki nie ma zawierać cudzysłowu, należy użyć nowego parametru **%MODULE_RAW%.**
>
> Podczas tworzenia projektu, który wyprowadza bibliotekę DLL, ATL nie doda cudzysłowów do nazwy ścieżki, jeśli jest używany **%MODULE%** lub **%MODULE_RAW%.**

## <a name="see-also"></a>Zobacz też

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)
