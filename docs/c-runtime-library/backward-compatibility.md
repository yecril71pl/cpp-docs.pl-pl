---
title: Zgodność ze starszymi wersjami
description: Jak używać programu Microsoft OLDNAMES. Biblioteka LIB do mapowania nazw funkcji w celu zapewnienia zgodności z poprzednimi wersjami.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
ms.openlocfilehash: b09104a5cff4d8e4cc31f9cc4707e808988401d6
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590293"
---
# <a name="backward-compatibility"></a>Zgodność ze starszymi wersjami

W celu zapewnienia zgodności między wersjami produktów Biblioteka OLDNAMES. LIB mapuje stare nazwy na nowe nazwy. Na przykład `open` mapuje na `_open` . Musisz jawnie powiązać z OLDNAMES. LIB tylko w przypadku kompilowania z następującymi kombinacjami opcji wiersza polecenia:

- `/Zl` (Pomiń domyślną nazwę biblioteki z pliku obiektu) i `/Ze` (domyślnie — Użyj rozszerzeń Microsoft)

- `/link` (kontrolka konsolidatora), `/NOD` (brak wyszukiwania biblioteki domyślnej) i `/Ze`

Aby uzyskać więcej informacji na temat opcji wiersza polecenia kompilatora, zobacz [Dokumentacja kompilatora](../build/reference/compiler-options.md).

## <a name="see-also"></a>Zobacz też

[Zgodność](../c-runtime-library/compatibility.md)
