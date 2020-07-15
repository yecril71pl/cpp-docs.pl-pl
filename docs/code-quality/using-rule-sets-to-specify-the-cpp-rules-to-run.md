---
title: Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia
ms.date: 07/13/2020
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.native
ms.openlocfilehash: 8b6d3fe8c8e441d4b233f2f4008d8aae9225726f
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373856"
---
# <a name="use-rule-sets-to-specify-the-c-rules-to-run"></a>Korzystanie z zestawów reguł do określania reguł C++ do uruchomienia

W programie Visual Studio można utworzyć i zmodyfikować niestandardowy *zestaw reguł* , aby spełniał wymagania dotyczące projektu związane z analizą kodu. Domyślne zestawy reguł są przechowywane w `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets` .

**Program Visual Studio 2017 w wersji 15,7 lub nowszej:** Zestawy reguł niestandardowych można utworzyć przy użyciu dowolnego edytora tekstu i zastosować je w przypadku kompilacji w wierszu polecenia niezależnie od tego, jakiego systemu kompilacji używasz. Aby uzyskać więcej informacji, zobacz [/analyze: reguł](/cpp/build/reference/analyze-code-analysis).

Aby utworzyć niestandardowy zestaw reguł języka C++ w programie Visual Studio, projekt C/C++ musi być otwarty w środowisku IDE programu Visual Studio. Następnie można otworzyć standardowy zestaw reguł w edytorze zestawu reguł, a następnie dodać lub usunąć określone reguły i opcjonalnie zmienić akcję, która występuje, gdy analiza kodu ustali, że reguła została naruszona.

Aby utworzyć nowy niestandardowy zestaw reguł, Zapisz go przy użyciu nowej nazwy pliku. Niestandardowy zestaw reguł jest automatycznie przypisywany do projektu.

## <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Aby utworzyć regułę niestandardową na podstawie jednego istniejącego zestawu reguł

1. W Eksplorator rozwiązań otwórz menu skrótów dla projektu, a następnie wybierz **Właściwości**.

1. Na karcie **Właściwości** wybierz pozycję **Analiza kodu**.

1. Z listy rozwijanej **zestaw reguł** wykonaj jedną z następujących czynności:

   - Wybierz zestaw reguł, który chcesz dostosować.

     \-oraz

   - Wybierz **\<Browse...>** , aby określić istniejący zestaw reguł, którego nie ma na liście.

1. Wybierz pozycję **Otwórz** , aby wyświetlić reguły w edytorze zestawu reguł.

## <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Aby zmodyfikować zestaw reguł w edytorze zestawu reguł

- Aby zmienić nazwę wyświetlaną zestawu reguł, w menu **Widok** wybierz polecenie **okno właściwości**. Wprowadź nazwę wyświetlaną w polu **Nazwa** . Zauważ, że nazwa wyświetlana może się różnić od nazwy pliku.

- Aby dodać wszystkie reguły grupy do niestandardowego zestawu reguł, zaznacz pole wyboru grupy. Aby usunąć wszystkie reguły grupy, usuń zaznaczenie pola wyboru.

- Aby dodać określoną regułę do niestandardowego zestawu reguł, zaznacz pole wyboru reguły. Aby usunąć regułę z zestawu reguł, usuń zaznaczenie pola wyboru.

- Aby zmienić akcję wykonywaną w przypadku naruszenia reguły w analizie kodu, wybierz pole **akcji** dla reguły, a następnie wybierz jedną z następujących wartości:

     **Ostrzeżenie** — generuje ostrzeżenie.

     **Błąd** — generuje błąd.

     **Info** — generuje komunikat.

     **Brak** — wyłącza regułę. Ta akcja jest taka sama jak usuwanie reguły z zestawu reguł.

## <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Aby grupować, filtrować lub zmieniać pola w edytorze zestawu reguł przy użyciu paska narzędzi edytora zestawu reguł

- Aby rozwinąć reguły we wszystkich grupach, wybierz **Rozwiń wszystkie**.

- Aby zwinąć reguły we wszystkich grupach, wybierz pozycję **Zwiń wszystko**.

- Aby zmienić pole, według którego reguły są grupowane, wybierz pole z listy **Grupuj według** . Aby wyświetlić reguły niezgrupowane, wybierz opcję **\<None>** .

- Aby dodać lub usunąć pola w kolumnach reguł, wybierz **Opcje kolumn**.

- Aby ukryć reguły, które nie mają zastosowania do bieżącego rozwiązania, wybierz **Ukryj reguły, które nie mają zastosowania do bieżącego rozwiązania**.

- Aby przełączać się między pokazywaniem i ukrywaniem reguł, które są przypisane do akcji błędu, wybierz **Pokaż reguły, które mogą generować błędy analizy kodu**.

- Aby przełączać się między pokazywaniem i ukrywaniem reguł, które są przypisane do akcji ostrzeżenie, wybierz **Pokaż reguły, które mogą generować ostrzeżenia analizy kodu**.

- Aby przełączać się między pokazywaniem i ukrywaniem reguł, do których przypisano akcję **Brak** , wybierz pozycję **Pokaż reguły, które nie są włączone**.

- Aby dodać lub usunąć zestawy reguł domyślnych firmy Microsoft do bieżącego zestawu reguł, wybierz pozycję **Dodaj lub usuń podrzędne zestawy reguł**.

## <a name="to-create-a-rule-set-in-a-text-editor"></a>Aby utworzyć zestaw reguł w edytorze tekstu

Można utworzyć niestandardowy zestaw reguł w edytorze tekstów, zapisać go w dowolnej lokalizacji z `.ruleset` rozszerzeniem i zastosować go przy użyciu opcji kompilatora [/analyze: zestaw reguł](/cpp/build/reference/analyze-code-analysis) .

Poniższy przykład przedstawia podstawowy plik zestawu reguł, którego można użyć jako punktu wyjścia:

::: moniker range="<=vs-2017"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

::: moniker range=">=vs-2019"

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

::: moniker-end

## <a name="ruleset-schema"></a>Schemat zestawu reguł

Poniższy schemat zestawu reguł zawiera opis schematu XML pliku zestawu reguł. Schemat zestawu reguł jest przechowywany w `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Schemas\RuleSet.xsd` . Można jej użyć do programistycznego tworzenia własnych zestawów reguł lub do sprawdzenia, czy niestandardowe zestaw reguł jest zgodny z prawidłowym formatem. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie dokumentu XML na podstawie schematu XSD](https://docs.microsoft.com/visualstudio/xml-tools/how-to-create-an-xml-document-based-on-an-xsd-schema?view=vs-2019).

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:annotation>
    <xs:documentation xml:lang="en">
            Visual Studio Code Analysis Rule Set Schema Definition Language.
            Copyright (c) Microsoft Corporation. All rights reserved.
        </xs:documentation>
  </xs:annotation>

  <!-- Every time this file changes, be sure to change the Validate method for the corresponding object in the code -->

  <xs:element name="RuleSet" type="TRuleSet">
  </xs:element>

  <xs:complexType name="TLocalization">
    <xs:all>
      <xs:element name="Name" type="TName" minOccurs="0" maxOccurs="1" />
      <xs:element name="Description" type="TDescription" minOccurs="0" maxOccurs="1" />
    </xs:all>
    <xs:attribute name="ResourceAssembly" type="TNonEmptyString" use="required" />
    <xs:attribute name="ResourceBaseName" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleHintPaths">
    <xs:sequence>
      <xs:element name="Path" type="TNonEmptyString" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="TName">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TDescription">
    <xs:attribute name="Resource" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TInclude">
    <xs:attribute name="Path" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TIncludeAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TIncludeAll">
    <xs:attribute name="Action" type="TIncludeAllAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRule">
    <xs:attribute name="Id" type="TNonEmptyString" use="required" />
    <xs:attribute name="Action" type="TRuleAction" use="required" />
  </xs:complexType>

  <xs:complexType name="TRules">
    <xs:sequence>
      <xs:element name="Rule" type="TRule" minOccurs="0" maxOccurs="unbounded" />
    </xs:sequence>
    <xs:attribute name="AnalyzerId" type="TNonEmptyString" use="required" />
    <xs:attribute name="RuleNamespace" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:complexType name="TRuleSet">
    <xs:sequence minOccurs="0" maxOccurs="1">
      <xs:element name="Localization" type="TLocalization" minOccurs="0" maxOccurs="1" />
      <xs:element name="RuleHintPaths" type="TRuleHintPaths" minOccurs="0" maxOccurs="1" />
      <xs:element name="IncludeAll" type="TIncludeAll" minOccurs="0" maxOccurs="1" />
      <xs:choice minOccurs="0" maxOccurs="unbounded">
        <xs:element name="Include" type="TInclude" minOccurs="0" maxOccurs="unbounded" />
        <xs:element name="Rules" type="TRules" minOccurs="0" maxOccurs="unbounded">
          <xs:unique name="UniqueRuleName">
            <xs:selector xpath="Rule" />
            <xs:field xpath="@Id" />
          </xs:unique>
        </xs:element>
      </xs:choice>
    </xs:sequence>
    <xs:attribute name="Name" type="TNonEmptyString" use="required" />
    <xs:attribute name="Description" type="xs:string" use="optional" />
    <xs:attribute name="ToolsVersion" type="TNonEmptyString" use="required" />
  </xs:complexType>

  <xs:simpleType name="TRuleAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
      <xs:enumeration value="None"/>
      <xs:enumeration value="Default"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TIncludeAllAction">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Error"/>
      <xs:enumeration value="Warning"/>
      <xs:enumeration value="Info"/>
      <xs:enumeration value="Hidden"/>
    </xs:restriction>
  </xs:simpleType>

  <xs:simpleType name="TNonEmptyString">
    <xs:restriction base="xs:string">
      <xs:minLength value="1" />
    </xs:restriction>
  </xs:simpleType>
  
</xs:schema>

```

Szczegóły elementu schematu:

| Element schematu | Opis |
|--------------------|--------------|
| `TLocalization` | Informacje o lokalizacji, w tym nazwa pliku zestawu reguł, Opis pliku z zestawem zasobów, Nazwa zespołu zawierającego zlokalizowany zasób i podstawowa nazwa zlokalizowanego zasobu |
| `TRuleHintPaths` | Ścieżki plików używane jako wskazówki do wyszukiwania plików zestawu reguł |
| `TName` | Nazwa bieżącego pliku zestawu reguł |
| `TDescription` | Opis bieżącego pliku zestawu reguł |
| `TInclude` | Ścieżka do dołączonego zestawu reguł z akcją reguły |
| `TIncludeAll` | Akcja reguły dla wszystkich reguł |
| `TRule` | Identyfikator reguły z akcją reguły |
| `TRules` | Kolekcja co najmniej jednej reguły |
| `TRuleSet` | Format pliku zestawu reguł, składający się z informacji o lokalizacji, ścieżek podpowiedzi reguły, obejmują wszystkie informacje, zawierają informacje, informacje o regułach, nazwę, opis i informacje o wersji |
| `TRuleAction` | Wyliczenie opisujące akcję reguły, taką jak błąd, ostrzeżenie, informacje, ukryte lub brak |
| `TIncludeAction` | Wyliczenie opisujące akcję reguły, taką jak błąd, ostrzeżenie, informacje, ukryte, brak lub domyślny |
| `TIncludeAllAction` | Wyliczenie opisujące akcję reguły, taką jak błąd, ostrzeżenie, informacje lub ukryte |

Aby zapoznać się z przykładem zestawu reguł, zobacz, [Aby utworzyć zestaw reguły w edytorze tekstu](#to-create-a-rule-set-in-a-text-editor), lub dowolny z domyślnych zestawów reguł przechowywanych w `%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule Sets` .
