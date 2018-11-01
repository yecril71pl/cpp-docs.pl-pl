---
title: Włączanie symboli udostępnionych (tylko do odczytu) lub obliczonych
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.shared.calculated
helpviewer_keywords:
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
ms.openlocfilehash: 9d57ceb202ce88a6668b8eb3cc93b41c1f11f2b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646004"
---
# <a name="including-shared-read-only-or-calculated-symbols"></a>Włączanie symboli udostępnionych (tylko do odczytu) lub obliczonych

Środowisko projektowe odczytuje plik zasobów utworzony przez inną aplikację po raz pierwszy oznacza wszystkie pliki nagłówkowe dołączone jako tylko do odczytu. Następnie możesz użyć [zasób zawiera okno dialogowe](../windows/resource-includes-dialog-box.md) można dodać dodatkowe symboli tylko do odczytu plików nagłówkowych.

Jest jednym z powodów warto używać definicje symboli tylko do odczytu dla plików symboli, które mają być udostępnianie dla kilku projektów.

Umożliwia także pliki symboli uwzględnione Jeśli masz istniejące zasoby dzięki definicje symboli, używające wyrażenia zamiast prostych liczb całkowitych do definiowania wartości symbolu. Na przykład:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)
```

Środowisko zostanie poprawnie interpretować te symbole obliczane tak długo, jak:

- Symbole obliczane są umieszczane w pliku symboli tylko do odczytu.

- Plik zasobów zawiera zasoby, do których te symbole obliczane są już przypisane.

- Oczekiwano wyrażenia liczbowego.

> [!NOTE]
> Jeśli oczekiwany jest ciąg lub wyrażenie numeryczne, wyrażenie nie jest oceniany.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Aby uwzględnić symbole udostępnione (tylko do odczytu) w pliku zasobów

1. W [widok zasobów](../windows/resource-view-window.md), kliknij prawym przyciskiem myszy plik .rc i wybierz [zasób zawiera](../windows/resource-includes-dialog-box.md) z menu skrótów.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. W **dyrektywy symboli tylko do odczytu** , używaj `#include` dyrektywy kompilatora, aby określić plik, którego symbole tylko do odczytu, które mają być przechowywane.

   Nie wywołuj pliku `Resource.h`, ponieważ jest to, nazwa_pliku zwykle używane przez plik nagłówka symbolu głównego.

   > [!NOTE]
   > **Ważne** wpisz w polu dyrektywy symboli tylko do odczytu jest zawarte w pliku zasobów, dokładnie tak, jak możesz wpisać. Upewnij się, w jakiej został wpisany nie zawiera błędów pisowni lub nieprawidłowa składnia.

   Użyj **dyrektywy symboli tylko do odczytu** pole, aby uwzględnić pliki przy użyciu tylko definicje symbolu. Nie zawierają definicje zasobów; w przeciwnym razie definicje zduplikowany zasób zostanie utworzony po zapisaniu pliku.

3. W pliku, który określiłeś, należy umieścić symbole.

   Symbole w plików znajdujących się w ten sposób są obliczane zawsze przy otwieraniu Twojego pliku zasobu, ale ich nie zostaną zastąpione na dysku po zapisaniu pliku.

4. Kliknij przycisk **OK**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Ograniczenia dotyczące nazwy symbolu](../windows/symbol-name-restrictions.md)<br/>
[Ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md)<br/>
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)<br/>
[Symbole: identyfikatory zasobów](../windows/symbols-resource-identifiers.md)