---
title: Błąd niekrytyczny ML A2006
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2006
helpviewer_keywords:
- A2006
ms.assetid: b8a8f096-95df-42b5-85ed-d2530560a84c
ms.openlocfilehash: 058100984acbd42ac2993732ab619c0a27c0edd2
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317087"
---
# <a name="ml-nonfatal-error-a2006"></a>Błąd niekrytyczny ML A2006

**Niezdefiniowany symbol: Identyfikator**

Podjęto próbę użycia niezdefiniowanego symbolu.

Może wystąpić jedna z następujących czynności:

- Symbol nie został zdefiniowany.

- Pole nie jest elementem członkowskim określonej struktury.

- Symbol został zdefiniowany w pliku dołączanym, który nie został uwzględniony.

- Symbol zewnętrzny został użyty bez dyrektywy [extern](extern-masm.md) lub [EXTERNDEF](externdef.md) .

- Nazwa symbolu jest błędna.

- Przywoływano lokalna etykieta kodu poza jej zakresem.

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)
