---
title: raw_method_prefix
ms.date: 08/29/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: b1bc536507716e5c117718ec825bf7fe76c84b61
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216146"
---
# <a name="raw_method_prefix"></a>raw_method_prefix

**C++Specjalne**

Określa inny prefiks, aby uniknąć kolizji nazw.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **raw_method_prefix (** "*prefix*" **)**

### <a name="parameters"></a>Parametry

*Prefiks*\
Prefiks, który ma być używany.

## <a name="remarks"></a>Uwagi

Właściwości i metody niskiego poziomu są uwidaczniane przez funkcje składowe o nazwie przy użyciu domyślnego prefiksu **raw_** , aby uniknąć kolizji nazw z funkcjami składowymi obsługi błędów wysokiego poziomu.

> [!NOTE]
> Skutki atrybutu **raw_method_prefix** są niezmienione przez obecność atrybutu [raw_interfaces_only](raw-interfaces-only.md) . **Raw_method_prefix** zawsze ma pierwszeństwo przed `raw_interfaces_only` określeniem prefiksu. Jeśli oba atrybuty są używane w tej samej `#import` instrukcji, zostanie użyty prefiks określony przez atrybut **raw_method_prefix** .

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
