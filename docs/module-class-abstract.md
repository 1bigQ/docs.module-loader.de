---
title: Abstrakte Modul Klassen
description: Aufbau und Programmierung von System-Modulen, Shipping-Modulen, Payment-Modulen und anderen Modulen für das modified Shop System.
---

# Modul Klasse

!!! note "Hinweis"

    In diesem Abschnitt schauen wir uns das Konzept der Modul Klasse im modified Shop System an. Es gibt "Konkrete Modul Klassen" oder "Modul Klassenerweiterungen". Diese Modul Klassen folgen alle dem gleichen Grundaufbau, den wir als Modul Klasse in dieser Dokumentation bezeichnen. 

In dieser Dokumentation führen wir eine klare Unterscheidung zwischen "Konkreten Modul Klassen" und "Modul Klassenerweiterungen" durch. Diese beiden Ansätze dienen dazu, das modified Shop System um neue Funktionalitäten zu erweitern und individuell anzupassen.

**Konkrete Modul Klassen:** Diese Art von Modul-Klassen fügt dem System spezifische Funktionalitäten hinzu, die oft in Form von Versandarten, Zahlungsmethoden oder ähnlichen Erweiterungen auftreten. Diese Klassen sind darauf ausgerichtet, bestimmte Aufgaben oder Prozesse innerhalb des Systems zu steuern und zu erweitern, und bieten somit eine gezielte Erweiterung der Shop-Funktionalität.

**Modul Klassenerweiterungen:** Im Gegensatz dazu ermöglichen Modul Klassenerweiterungen die Modifikation von bereits vorhandenen PHP-Klassen in modified, ähnlich wie es bei Hookpoints der Fall ist. Dieser Ansatz erlaubt es, bestehende Funktionalitäten anzupassen, zu erweitern oder zu verfeinern, indem spezifische Teile des Codes gezielt verändert werden. Dadurch kannst du die Flexibilität des Systems erhöhen und es an deine individuellen Anforderungen anpassen.

Die klare Unterscheidung zwischen diesen beiden Ansätzen ist entscheidend, um zu verstehen, wie du deine Modulentwicklung am besten strukturieren kannst. Je nach den Anforderungen deines Projekts kannst du entweder auf Konkrete Modul Klassen setzen, um gezielte Funktionen hinzuzufügen, oder Klassenerweiterungen verwenden, um bestehende Funktionen anzupassen und zu erweitern. Dies gibt dir die notwendige Flexibilität, um maßgeschneiderte Lösungen für deinen modified Shop zu entwickeln.

## Übersicht aller Modul Klassen

Im modified System gibt es eine Vielzahl von Modul Klassen, die in zwei Hauptkategorien unterteilt werden: Konkrete Modul Klassen und Modul Klassenerweiterungen. In diesem Abschnitt bieten wir eine grundlegende Übersicht über die gemeinsamen Strukturen und Konzepte, die diese Modul Klassen teilen. In weiteren Abschnitten werden wir die spezifischen Besonderheiten und Anwendungsfälle jeder einzelnen Modul Klasse ausführlich behandeln.

### Konkrete Modul Klassen

Die konkreten Modul Klassen sind darauf ausgerichtet, spezifische Funktionen und Erweiterungen in das modified System einzuführen, um verschiedene Aspekte des Shops anzupassen und zu erweitern.

- [System](#): Diese Klasse ermöglicht grundlegende Steuerung und Einstellungen von Modulen.

- [Shipping](#): Mit dieser Klasse kannst du Versandmethoden und -optionen verwalten und an individuelle Anforderungen anpassen.

- [Payment](#): Hiermit werden Zahlungsmethoden integriert und konfiguriert, um eine reibungslose Abwicklung von Zahlungen im Shop zu gewährleisten.

- [Export](#): Diese Klasse bietet Funktionen zur Datenausgabe und ermöglicht die Anpassung von Exportprozessen.

- [OrderTotal](#): Diese Klasse gestattet die Berechnung und Anzeige von Bestellsummen und anderen relevanten Informationen.

### Modul Klassenerweiterungen

Modul Klassenerweiterungen hingegen konzentrieren sich darauf, bestehende PHP-Klassen in modified anzupassen und zu erweitern, um die Funktionalität des Shops individuell anzupassen.

- [Categories](#): Diese Erweiterung ermöglicht die Anpassung und Erweiterung von Kategoriefunktionen im Shop.

- [Checkout](#): Hier werden Prozesse im Checkout-Bereich angepasst, um den Bestellvorgang optimal zu gestalten.

- [Main](#): Diese Klassenerweiterung bietet Möglichkeiten zur Anpassung der Hauptfunktionalitäten des Shops.

- [Order](#): Mit dieser Erweiterung kannst du Bestellungen individuell anpassen.

- [Product](#): Hier werden Möglichkeiten geboten, Produkteigenschaften und -anzeigen zu erweitern und anzupassen.

- [ShoppingCart](#): Diese Klasse erlaubt die Anpassung des Warenkorbverhaltens und der Warenkorbfunktionen.

- [XtcPrice](#): Hier werden Preisberechnungen und Preisanzeigen individuell gestaltet und angepasst.

Die Übersicht über diese Modul Klassen dient dir als Orientierungshilfe, um die geeignete Modul Klasse für deine spezifischen Anforderungen zu finden.

## Das allgemeine Konzept von konkreten Modul Klassen und Modul Klassenerweiterungen

Mit einer Modul Klassen lässt sich das modified Shop System erweitern. Die Modul Klassen werden vom System für unterschiedliche Aufgaben geladen. Mit ihnen können wie bereits geschrieben z. B. Verstand und Zahlungsmodule realisiert werden oder das Verhalten vom Warenkorb verändert werden. Zudem bieten sie einen Anlaufpunkt für Einstellungen, die ein User im Adminbereich zum jeweiligen Modul tätigen kann.

## Der Aufbau von Modul Klassen

### Dateien

Eine Modul Klasse besteht in der Regel aus mindestens zwei Dateien: einer PHP-Datei mit der Klassen-Definition und einer Sprachdatei.

!!! note "Hinweis"

    Das modified System lädt automatisch ein stylesheet für deine Moduleinstellungen (im Adminbereich), soweit es existiert und als Dateinamen den Modulnamen trägt.

- PHP-Klassen-Definition: Die PHP-Datei befindet sich je nach Modultyp im Verzeichnis `/includes/modules/<TYPE>/` oder `/admin/includes/modules/<TYPE>/`.

- Sprachdatei: Jede verfügbare Sprache hat eine entsprechende PHP-Datei im Verzeichnis `/lang/<LANGUAGE>/modules/<TYPE>/`.

Eine Liste mit allen Modul Klassen und deren Methoden, die du erweitern kannst, findest du unter [github.com/RobinTheHood/class-extensions](https://github.com/RobinTheHood/class-extensions)

### PHP-Datei zu Modul Klasse

Eine Modul Klasse sollte genau eine PHP-Klasse enthalten. Diese Klasse muss den gleichen Namen haben (ohne .php), wie die Datei, in der sie sich befindet. Als Beispiel nehmen wir eine Datei mit dem Namen `mc_my_first_module.php`. Die entsprechende PHP-Klasse müsste also `mc_my_first_module` heißen. Das Einhalten dieser Namenskonvention ist entscheidend, da der Klassenloader im modified Core die Datei ansonsten nicht in den Speicher lädt und die Klasse nicht verwendet werden kann.

!!! note "Hinweis"
    Leider haben in modified einige Modul Klassen eigene Namenskonventionen. Schau dir dazu die Information der jeweiligen Modul Klasse in dieser Dokumentation an.

In dieser Dokumentation zeigen wir dir zwei Ansätze zur Erstellung von Modul Klassen. Ohne und mit dem StdModul:

- Ohne StdModul - Wenn du eine Modul Klasse ohne Hilfsklassen erstellen möchtest, kannst du den Beispielcode am Ende dieses Abschnitts als Ausgangspunkt verwenden und ihn an deine Anforderungen anpassen. Dieser Ansatz bietet folgende Vor- und Nachteile:

**Vorteile:**

1. **Maximale Flexibilität:** Die Verwendung von Modul Klassen ohne StdModul bietet maximale Flexibilität, da du die gesamte Logik und Struktur des Moduls von Grund auf neu gestalten kannst. Dies ermöglicht eine maßgeschneiderte Anpassung an spezifische Anforderungen.

2. **Keine unnötigen Abhängigkeiten:** Du vermeidest die Einführung unnötiger Abhängigkeiten von Hilfsklassen.

3. **Keine Einschränkungen bei der Implementierung:** Du kannst deine eigene Logik und Implementierung wählen, ohne auf die Vorgaben einer Standard-Hilfsklasse Rücksicht nehmen zu müssen.

**Nachteile:**

1. **Mehr Entwicklungszeit:** Da du jeden Aspekt des Moduls von Grund auf neu entwickeln musst, kann dies mehr Zeit in Anspruch nehmen und die Entwicklungszeit verlängern.

2. **Potenziell komplexer Code:** Ohne die vorgefertigten Strukturen und Methoden eines Hilfsklassen-Frameworks kann der Code komplexer werden, was die Wartbarkeit und Erweiterbarkeit erschweren kann.

3. **Höheres Risiko von Fehlern:** Bei der manuellen Implementierung aller Funktionen besteht ein höheres Risiko von Fehlern und Inkonsistenzen im Code, was zu unerwartetem Verhalten führen kann.

Insgesamt bietet der Ansatz "Ohne StdModul" maximale Freiheit bei der Modulentwicklung, erfordert jedoch in der Regel mehr Entwicklungszeit und erhöht das Risiko von Fehlern.


- Mit StdModul - Wenn du eine Modul Klasse mit der Hilfsklasse StdModul erstellen möchtest, kannst du den Beispielcode am Ende dieses Abschnitts als Basis verwenden und an deine Bedürfnisse anpassen. Dieser Ansatz bietet folgende Vor- und Nachteile:

**Vorteile:**

1. **Zeitersparnis:** Die Verwendung von StdModul als Hilfsklasse kann die Entwicklungszeit erheblich verkürzen, da sie bereits vordefinierte Strukturen und Methoden für die Modulentwicklung bereitstellt. Dies beschleunigt die Implementierung erheblich.

2. **Konsistenz und Einheitlichkeit:** StdModul fördert die Einheitlichkeit im Code, da es klare Richtlinien und Strukturen vorgibt. Dies erleichtert die Wartung und Zusammenarbeit im Team.

3. **Verminderte Fehleranfälligkeit:** Da StdModul bewährte Praktiken und Best Practices implementiert, werden Fehler und Inkonsistenzen in der Modulentwicklung reduziert, was zu einer höheren Codequalität führt.

**Nachteile:**

1. **Geringere Flexibilität:** Die Verwendung von StdModul kann die Flexibilität bei der Modulentwicklung einschränken, da Entwickler innerhalb der vorgegebenen Strukturen arbeiten müssen. Dies kann zu Einschränkungen bei der Anpassung an sehr spezifische Anforderungen führen.

2. **Abhängigkeit von externer Struktur:** Bei Verwendung von StdModul sind Module an eine externe Struktur gebunden, was bedeutet, dass Änderungen an dieser Struktur möglicherweise erforderlich sind, um die Module ordnungsgemäß funktionieren zu lassen.

3. **Einschränkungen bei der Erweiterbarkeit:** Da die Methoden und Funktionalitäten von StdModul vorgegeben sind, kann es schwierig sein, zusätzliche Funktionen oder Erweiterungen zu implementieren, die über den Umfang der Hilfsklasse hinausgehen.

Insgesamt bietet der Ansatz "Mit StdModul" eine beschleunigte Entwicklung und verbesserte Codequalität, jedoch auf Kosten einer gewissen Einschränkung der Flexibilität und Anpassungsfähigkeit.


=== "Ohne StdModule"

    ```php title="mc_my_first_module.php"
    <?php

    declare(strict_types=1);

    defined('_VALID_XTC') or die('Direct Access to this location is not allowed.');

    class mc_my_first_module
    {
        ...
    }
    ```

=== "Mit StdModule"

    ```php title="mc_my_first_module.php"
    <?php

    declare(strict_types=1);

    use RobinTheHood\ModifiedStdModule\Classes\StdModule;

    class mc_my_first_module extends StdModul
    {
        ...
    }
    ```

### Voraussetzungen für Modul Klassen

Eine Modul-Datei besteht meistens aus den folgenden Elementen:

#### Attribute

- `public string $code`
- `public string $title`
- `public string $description`
- `public bool $enabled`
- `public int $sort_order`

#### Methoden

- `public function __construct()`
- `public function keys(): array`
- `public function check(): int`
- `public function install(): void`
- `public function remove(): void`

Eine ausführliche Beschreibung, was die jeweiligen Aufgaben dieser Elemente sind, findest du im Abschnitt [Referenzen > Modul Klasse](/references/module-class/). Wir gehen hier hauptsächlich auf die Methode `__construct()` ein.


### Der Constructor - in einfacher Form (nicht verwenden)

??? note "Textstatus - Entwurf"

    Status: 2 von 5 - Erster Entwurf: Erste Ausformulierung einiger Informationen.

Als Erstes erklären wir dir die Aufgabe des Contructors anhand eines einfachen Beispiels. Dieses Beispiel solltest du in dieser Form aber nicht verwenden. Das Modul ist so nicht mehrsprachig und kann auch nicht über das Admininterface vom Nutzer aktiviert oder deaktiviert werden, da der Wert für `$this->enabled` immer auf `true` steht.

Im Constructor müssen wir jetzt die Attribute mit Werte füllen. Wir könnten für viele Attribute feste Werte verwenden.

```php title="mc_my_first_module.php"
public function __construct()
{
    $this->code        = 'mc_my_first_module';
    $this->title       = 'Mein ersten Modul von My Company';
    $this->description = 'Das ist mein ersten Modul. Es ...';
    $this->sort_order  = 0;
    $this->enabled     = true;
}
```

### Der Constructor - mehrsprachig und dynamisch

??? note "Textstatus - Entwurf"

    Status: 2 von 5 - Erster Entwurf: Erste Ausformulierung einiger Informationen.

Um die Unzulänglichkeiten aus dem ersten Constructor Beispiel zu umgehen, schauen wir uns jetzt an, wie wir dieses besser machen könnten.

=== "Ohne StdModule"

    ```php title="mc_my_first_module.php"
    public function __construct()
    {
        // Der Wert in $this->prefix ist: MODULE_MC_MY_FIRST_MODULE
        $this->prefix = 'MODULE_' . strtoupper(self::class);

        $this->code        = self::class;
        $this->title       = constant($this->prefix . '_TITLE');
        $this->description = constant($this->prefix . '_DESC');
        $this->sort_order  = constant($this->prefix . '_SORT_ORDER');
        $this->enabled     = defined($this->prefix . '_STATUS') && 'true' === constant($this->prefix . '_STATUS');
    }
    ```

=== "Mit StdModule"

    ```php title="mc_my_first_module.php"
    public function __construct()
    {
        parent::__construct('MODULE_MC_MY_FIRST_MODULE');
    }
    ```

Statt feste Werte für `$this->title` und `$this->description`, holen wir uns diese Werte aus Konstanten, die wir später in einer Sprachdatei definieren. Siehe hierfür den Abschnitt [???](#).

Den vorderen Teil der Konstanten `MODULE_MC_MY_FIRST_MODULE` lassen wir uns bequem automatisch erzeugen und speichern in der Variablen `$prefix` zwischen.

```php
$prefix = 'MODULE_' . strtoupper(self::class);
```

Die Konstanten `MODULE_MC_MY_FIRST_MODULE_SORT_ORDER` und `MODULE_MC_MY_FIRST_MODULE_STATUS` lädt der modified Core für uns aus der Datenbanktabelle `configure`, bevor er versucht eine Instanz der Klasse zu erzeugen und der Constructor aufgerufen wird.

Wie wir die Konstanten in die Datenbank bekommen, schauen wir uns auch noch an. Das passiert automatisch vom modified Core, sobald die Funktion `install()` aufgerufen wird, wie wir uns auch gleich noch anschauen werden.

## Beispiel

=== "Ohne StdModule"

    ```php title="mc_my_first_module.php"
    <?php

    declare(strict_types=1);

    defined('_VALID_XTC') or die('Direct Access to this location is not allowed.');

    class mc_my_first_module
    {
        /** @var string $prefix **/
        public $prefix;

        /** @var string $code **/
        public $code;

        /** @var string $title **/
        public $title;

        /** @var string $description **/
        public $description;

        /** @var bool $enabled **/
        public $enabled;

        /** @var int $sort_order **/
        public $sort_order;

        /** @var string[] $keys **/
        public $keys;

        public function __construct()
        {
            // Der Wert in $prefix ist: MODULE_MC_MY_FIRST_MODULE
            $this->prefix = 'MODULE_' . strtoupper(self::class);

            $this->code        = self::class;
            $this->title       = constant($this->prefix . '_TITLE');
            $this->description = constant($this->prefix . '_DESC');
            $this->sort_order  = constant($this->prefix . '_SORT_ORDER');
            $this->enabled     = defined($this->prefix . '_STATUS') && 'true' === constant($this->prefix . '_STATUS');
        }

        /**
         * @return string[]
         */
        public function keys(): array
        {
            return [];
        }

        public function check(): int
        {

            $key = $this->prefix . '_STATUS';

            $query = xtc_db_query(
                "SELECT configuration_value FROM " . TABLE_CONFIGURATION . " WHERE configuration_key = '$key'"
            );

            return xtc_db_num_rows($query);
        }

        public function install(): void
        {
            $this->addConfiguration('STATUS', 'true', 6, 1, "xtc_cfg_select_option(array('true', 'false'),");
        }

        public function remove(): void
        {
            $this->deleteConfiguration('STATUS');
        }

        protected function addConfiguration(
            string $key,
            string $value,
            int $groupId,
            int $sortOrder,
            string $setFunction = '',
            string $useFunction = ''
        ): void {
            $key = $this->prefix . '_' . $key;
            $setFunction = str_replace("'", "\\'", $setFunction);
            xtc_db_query("INSERT INTO `" . TABLE_CONFIGURATION . "` (`configuration_key`, `configuration_value`, `configuration_group_id`, `sort_order`, `set_function`, `use_function`, `date_added`) VALUES ('$key', '$value', '$groupId', '$sortOrder', '$setFunction', '$useFunction', NOW())");
        }

        protected function deleteConfiguration(string $key): void
        {
            $key = $this->prefix . '_' . $key;
            xtc_db_query("DELETE FROM " . TABLE_CONFIGURATION . " WHERE configuration_key = '$key'");
        }
    }
    ```

=== "Mit StdModule"

    ```php title="mc_my_first_module.php"
    <?php

    declare(strict_types=1);

    use RobinTheHood\ModifiedStdModule\Classes\StdModule;

    class mc_my_first_module extends StdModule
    {

        public function __construct()
        {
            parent::__construct('MODULE_MC_MY_FIRST_MODULE');
        }

        public function install(): void
        {
            parent::install();
        }

        public function uninstall(): void
        {
            parent::uninstall();
        }
    }
    ```

## Namenskonventionen für Modul Klassen - Beispiele

??? note "Textstatus - Entwurf"

    Status: 2 von 5 - Erster Entwurf: Erste Ausformulierung einiger Informationen.

### Modul Klassen

- Der Dateiname gibt vor, wie der Klassenname ist.
- Der Klassenname gibt vor, wie der Sprachdateiname ist.
- Der Klassenname und Typ geben vor, wie der Name der Konfigurations-Konstante ist.
- Achtung: Bei Shipping Modul Klassen gibt es eine Ausnahme. Diese dürfen kein `_` im Namen haben.


#### snake_case

| Type     | File                  | Lang File             | Class             | Const                           |
|----------|-----------------------|-----------------------|-------------------|---------------------------------|
| system   | system_mc_my_first_module.php  | system_mc_my_first_module.php  | system_mc_my_first_module  | MODULE_SYSTEM_MC_MY_FIRST_MODULE_STATUS  |
| export   | export_mc_my_first_module.php  | export_mc_my_first_module.php  | export_mc_my_first_module  | MODULE_EXPORT_MC_MY_FIRST_MODULE_STATUS  |
| shipping | shippingmcmyfirstmodule.php  | shippingmcmyfirstmodule.php  | shippingmcmyfirstmodule  | MODULE_SHIPPING_MCMYFIRSTMODULE_STATUS |
| payment  | payment_mc_my_first_module.php | payment_mc_my_first_module.php | payment_mc_my_first_module | MODULE_PAYMENT_MC_MY_FIRST_MODULE_STATUS |
| order_total | ot_mc_my_first_module.php | ot_mc_my_first_module.php | ot_mc_my_first_module | MODULE_ORDER_TOTAL_MC_MY_FIRST_MODULE_STATUS |

#### PascalCase

!!! note "Hinweis"

    Technisch ist es möglich, dass Klassen- und Dateinamen auch in `PascalCase` geschrieben werden. Wir empfehlen zurzeit die Schreibweise in `snake_case`.

| Type     | File                  | Lang File             | Class             | Const                            |
|----------|-----------------------|-----------------------|-------------------|----------------------------------|
| system   | SystemMcMyFirstModule.php    | SystemMcMyFirstModule.php    | SystemMcMyFirstModule    | MODULE_SYSTEM_MC_MY_FIRST_MODULE_STATUS   |
| export   | ExportMcMyFirstModule.php    | ExportMcMyFirstModule.php    | ExportMcMyFirstModule    | MODULE_EXPORT_MC_MY_FIRST_MODULE_STATUS   |
| shipping | ShippingMcMyFirstModule.php  | ShippingMcMyFirstModule.php  | ShippingMcMyFirstModule  | MODULE_SHIPPING_MC_MY_FIRST_MODULE_STATUS |
| payment  | PaymentMcMyFirstModule.php   | PaymentMcMyFirstModule.php   | PaymentMcMyFirstModule   | MODULE_PAYMENT_MC_MY_FIRST_MODULE_STATUS  |
| order_total |  🚫   | 🚫 | 🚫  | 🚫 |


### Klassenerweiterungen

- Der Dateiname gibt vor, wie der Klassenname ist.
- Der Klassenname gibt vor, wie der Sprachdateiname ist.
- Der Klassenname und Typ geben vor, wie der Name der Konfigurations-Konstante ist.

#### snake_case

| Type          | File                        | Lang File                   | Class                   | Const                                 |
|---------------|-----------------------------|-----------------------------|-------------------------|---------------------------------------|
| categories    | categories_mc_my_first_module.php    | categories_mc_my_first_module.php    | categories_mc_my_first_module    | MODULE_CATEGORIES_MC_MY_FIRST_MODULE_STATUS    |
| checkout      | checkout_mc_my_first_module.php      | checkout_mc_my_first_module.php      | checkout_mc_my_first_module      | MODULE_CHECKOUT_MC_MY_FIRST_MODULE_STATUS      |
| main          | main_mc_my_first_module.php          | main_mc_my_first_module.php          | main_mc_my_first_module          | MODULE_MAIN_MC_MY_FIRST_MODULE_STATUS          |
| order         | order_mc_my_first_module.php         | order_mc_my_first_module.php         | order_mc_my_first_module         | MODULE_ORDER_MC_MY_FIRST_MODULE_STATUS         |
| product       | product_mc_my_first_module.php       | product_mc_my_first_module.php       | product_mc_my_first_module       | MODULE_PRODUCT_MC_MY_FIRST_MODULE_STATUS       |
| shopping_cart | shopping_cart_mc_my_first_module.php | shopping_cart_mc_my_first_module.php | shopping_cart_mc_my_first_module | MODULE_SHOPPING_CART_MC_MY_FIRST_MODULE_STATUS |
| xtcPrice      | xtcprice_mc_my_first_module.php      | xtcprice_mc_my_first_module.php      | xtcPrice_mc_my_first_module      | MODULE_XTCPRICE_MC_MY_FIRST_MODULE_STATUS      |

#### PascalCase

!!! note "Hinweis"

    Technisch ist es möglich, dass Klassen- und Dateinamen auch in `PascalCase` geschrieben werden. Wir empfehlen zurzeit die Schreibweise in `snake_case`.

| Type          | File                     | Lang File                | Class                | Const                                 |
|---------------|--------------------------|--------------------------|----------------------|---------------------------------------|
| categories    | CategoriesMcMyFirstModule.php   | CategoriesMcMyFirstModule.php   | CategoriesMcMyFirstModule   | MODULE_CATEGORIES_MC_MY_FIRST_MODULE_STATUS    |
| checkout      | checkoutMcMyFirstModule.php     | checkoutMcMyFirstModule.php     | checkoutMcMyFirstModule     | MODULE_CHECKOUT_MC_MY_FIRST_MODULE_STATUS      |
| main          | MainMcMyFirstModule.php         | MainMcMyFirstModule.php         | MainMcMyFirstModule         | MODULE_MAIN_MC_MY_FIRST_MODULE_STATUS          |
| order         | OrderMcMyFirstModule.php        | OrderMcMyFirstModule.php        | OrderMcMyFirstModule        | MODULE_ORDER_MC_MY_FIRST_MODULE_STATUS         |
| product       | ProductMcMyFirstModule.php      | ProductMcMyFirstModule.php      | ProductMcMyFirstModule      | MODULE_PRODUCT_MC_MY_FIRST_MODULE_STATUS       |
| shopping_cart | ShoppingCartMcMyFirstModule.php | ShoppingCartMcMyFirstModule.php | ShoppingCartMcMyFirstModule | MODULE_SHOPPING_CART_MC_MY_FIRST_MODULE_STATUS |
| xtcPrice      | XtcpriceMcMyFirstModule.php     | XtcpriceMcMyFirstModule.php     | XtcpriceMcMyFirstModule     | MODULE_XTCPRICE_MC_MY_FIRST_MODULE_STATUS      |

### Autoinclude

| Type     | File          |
|----------|---------------|
| autoload | mc_my_first_module.php |

### Template

| Type     | File          |
|----------|---------------|
| template | mc_my_first_module.php |
