---
title: Kreator dodawania zmiennej członkowskiej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.variable.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Member Variable Wizard [C++]
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e53f9075648d5ea0d2c02e98be30c3c43a87f335
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396808"
---
# <a name="add-member-variable-wizard"></a>Kreator dodawania zmiennej członkowskiej

Ten kreator dodaje deklaracji zmiennej składowej do pliku nagłówka, a następnie w zależności od opcji go dodać kod do pliku .cpp. Po dodaniu zmiennej składowej, za pomocą kreatora można edytować kod w środowisku programistycznym.

- **Dostęp do**

   Ustawia dostęp do zmiennej elementu członkowskiego. Modyfikatory dostępu są słowami kluczowymi, określające dostęp, innych klas, że zmienna członka. Zobacz [kontroli dostępu do elementu członkowskiego](../cpp/member-access-control-cpp.md) Aby uzyskać więcej informacji na temat określania dostępu. Poziom dostępu do zmiennej elementu członkowskiego jest równa **publicznych** domyślnie.

- [public](../cpp/public-cpp.md)

- [protected](../cpp/protected-cpp.md)

- [private](../cpp/private-cpp.md)

- **Typ zmiennej**

   Ustawia typ zwrotny dla zmiennej elementu członkowskiego, który dodajesz.

   - W przypadku dodawania zmiennej członkowskiej, która nie jest kontrolka okna dialogowego wybierz z listy dostępnych typów.

      Aby uzyskać informacje o typach, zobacz [podstawowych typów](../cpp/fundamental-types-cpp.md).

      |||
      |-|-|
      |**char**|**short**|
      |**double**|**unsigned char**|
      |**float**|**unsigned int**|
      |**int**|**unsigned long**|
      |**long**||

   - W przypadku dodawania zmiennej składowej formantu pola okna dialogowego, to pole jest wypełniane przy użyciu typu obiektu, dla formantu lub wartości zwracane. Jeśli wybierzesz **kontroli**, następnie **typ zmiennej** Określa klasę bazową formantu wybierz w **identyfikator formantu** pole. Jeśli kontrolka okna dialogowego może zawierać wartość, a jeśli wybierzesz **wartość**, następnie **typ zmiennej** określa odpowiedniego typu dla wartości, który może zawierać kontrolki. Zobacz [formantów okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md) Aby uzyskać więcej informacji.

      Ta wartość jest zależna od zaznaczenia w **identyfikator formantu** i nie można zmienić.

- **Nazwa zmiennej**

   Określa nazwę zmiennej elementu członkowskiego, który dodajesz. Zmienne Członkowskie zazwyczaj rozpoczynają się od ciągu identyfikujący "m_", która domyślnie jest udostępniany dla Ciebie.

- **Zmienna sterująca**

   Wskazuje, że zmiennej składowej zarządza formantu w oknie dialogowym z [wymiany danych i sprawdzanie poprawności danych](../mfc/dialog-data-exchange-and-validation.md) pomocy technicznej. Zobacz [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) Aby uzyskać więcej informacji. Ta opcja jest dostępna tylko w przypadku zmienne Członkowskie dodane do klasy pochodne [CDialog](../mfc/reference/cdialog-class.md). Zaznacz to pole, aby aktywować **Identyfikator kontrolki** i **kontrolowanie typu** opcje.

- **Identyfikator formantu**

   Ustawia identyfikator dla zmiennej formantu, którego dodajesz. Wybierz z listy identyfikator typu formantu, dodawania zmiennej składowej. Lista jest aktywny tylko wtedy, gdy **zmienna sterująca** pole jest zaznaczone, a maksymalna długość to identyfikatory dla formantów już dodana do okna dialogowego. Na przykład w przypadku standardowych **OK** jest identyfikator formantu przycisku **IDOK**.

   |Opcja|Opis|
   |------------|-----------------|
   |**Kontrolki**|Ta opcja jest ustawiona domyślnie dla kontrolek typu. (Jak warto zrobić za pomocą pola listy, pola kombi lub pola edycji) zarządza kontroli się i nie stanu lub zawartość formantu.|
   |**Wartość**|Ta opcja jest dostępna tylko dla typów formantów, które zawiera wartość (na przykład pole edycji) lub odzwierciedla stan (na przykład pole wyboru) i dla których może zarządzać zakresu, zawartości lub stanu. Zobacz [formantów okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md) Aby uzyskać więcej informacji.|

- **Kategoria**

   Określa, czy zmienna jest oparta na typie kontrolki lub wartość formantu.

- **Typ formantu**

   Ustawia typ kontroli dodawany. To pole nie jest dostępna. Na przykład przycisk ma typ formantu **przycisk**, i pole kombi typu formantu **COMBOBOX**. Zobacz [formantów okna dialogowego i typy zmiennych](../ide/dialog-box-controls-and-variable-types.md) Aby uzyskać więcej informacji.

- **Maksymalna liczba znaków**

   Dostępne tylko wtedy, gdy **typ zmiennej** ustawiono [CString](../atl-mfc-shared/reference/cstringt-class.md). Wskazuje maksymalną liczbę znaków, które może zawierać kontrolki.

- **Wartość minimalna**

   Dostępne tylko wtedy, gdy typ zmiennej jest **BOOL**, `int`, **UINT**, **długie**, `DWORD`, **float**, **double**, **BAJTÓW**, **krótki**, [COLECurrency](../mfc/reference/colecurrency-class.md) lub [CTime](../atl-mfc-shared/reference/ctime-class.md). Wskazuje najniższej wartości dopuszczalne w zakresie skalowania lub daty.

- **Wartość maksymalna**

   Dostępne tylko wtedy, gdy typ zmiennej jest **BOOL**, `int`, **UINT**, **długie**, `DWORD`, **float**, **double**, **BAJTÓW**, **krótki**, `COLECurrency` lub `CTime`. Wskazuje najwyższej wartości dopuszczalne w zakresie skalowania lub daty.

- **plik .h**

   Dla formantów ActiveX, których zmienne Członkowskie wymagają klasy otoki. Określa nazwę pliku nagłówka, aby dodać deklaracji klasy.

- **Plik CPP**

   Dla formantów ActiveX, których zmienne Członkowskie wymagają klasy otoki. Określa nazwę pliku implementacji, aby dodać definicję klasy.

- **Komentarz**

   Zawiera komentarz w pliku nagłówkowym zmiennej elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)