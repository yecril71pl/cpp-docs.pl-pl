---
title: Błąd CXX0065 programu Expression Evaluator
ms.date: 11/04/2016
f1_keywords:
- CXX0065
helpviewer_keywords:
- CAN0065
- CXX0065
ms.assetid: aac68f87-0b90-4c19-afa6-1c587625a5fd
ms.openlocfilehash: b4120deec3c8e7ce14e381f782904cf83a588e43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184427"
---
# <a name="expression-evaluator-error-cxx0065"></a>Błąd CXX0065 programu Expression Evaluator

Zmienna wymaga ramki stosu

Wyrażenie zawiera zmienną, która istnieje w bieżącym zakresie, ale nie została jeszcze utworzona.

Ten błąd może wystąpić, gdy nastąpiło przeprowadzenie prologu funkcji, ale nie skonfigurowano jeszcze ramki stosu dla funkcji lub jeśli nastąpiło przeprowadzenie kodu zakończenia dla funkcji.

Przechodzenie przez kod prologu do momentu skonfigurowania ramki stosu przed rozpoczęciem oceny wyrażenia.

Ten błąd jest identyczny z CAN0065.
