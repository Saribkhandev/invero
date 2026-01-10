# How to Set Up Dynamic Supplement Facts

To make the Supplement Facts popup fully dynamic for every product (matching the AG1 reference), you need to define specific **Metaobjects** and **Product Metafields** in your Shopify Admin.

## Step 1: Create the Metaobject Definition

This controls the individual rows (nutrients, complexes, ingredient lists).

1.  Go to **Settings > Custom Data > Metaobjects**.
2.  Click **Add definition**.
3.  **Name**: `Supplement Fact Row`
4.  **Type**: `supplement_fact_row` (automatically set usually)
5.  Add the following **Fields**:

    | Field Name | Type | Key (Keep exact) | Description |
    | :--- | :--- | :--- | :--- |
    | **Name** | Single line text | `name` | e.g., "Vitamin C" or "Active Superfood Complex" |
    | **Amount** | Single line text | `amount` | e.g., "420mg" or "7.5g" |
    | **Daily Value** | Single line text | `daily_value` | e.g., "467%", "†", or leave blank |
    | **Is Indented** | True or false | `is_indented` | Check if this is a sub-item (like "Dietary Fiber") |
    | **Divider Style** | Single line text (Preset choices) | `divider_style` | **Recommended:** Select "Limit to preset choices" and add: "Thick", "Thin", "None". |
    | **Description** | Rich text | `description` | **Crucial**: Use this for the long ingredient lists below headers like "Active Superfood Complex". |

## Step 2: Create Product Metafields

These fields attach the data to your actual Products.

1.  Go to **Settings > Custom Data > Products**.
2.  **Add Definition** for each of the following:

    ### A. The Rows List
    *   **Name**: Supplement Facts Rows
    *   **Namespace and key**: `custom.supplement_facts`
    *   **Type**: Metaobject
    *   **Reference**: Select `Supplement Fact Row`
    *   **List**: **Check "List of entries"** (Important!)

    ### B. Serving Size
    *   **Name**: Serving Size
    *   **Namespace and key**: `custom.serving_size`
    *   **Type**: Single line text
    *   **Description**: e.g., "1 Scoop (12g)"

    ### C. Servings Per Container
    *   **Name**: Servings Per Container
    *   **Namespace and key**: `custom.servings_per_container`
    *   **Type**: Single line text
    *   **Description**: e.g., "30"

    ### D. Footer Notes
    *   **Name**: Supplement Facts Footer
    *   **Namespace and key**: `custom.supplement_facts_footer`
    *   **Type**: Rich text
    *   **Description**: Use this for the "* Percent Daily Value...", "Contains: Soy", and "Other Ingredients" section.

## Step 3: Managing Content

1.  Go to a **Product** in your admin.
2.  Scroll to **Metafields**.
3.  **Serving Size**: Enter "1 Scoop (12g)".
4.  **Supplement Facts Rows**: Click to add entries.
    *   For a simple row: Name="Calories", Amount="50".
    *   For a section divider: Name="Active Superfood Complex", Amount="7.5g", Divider Style="Thick".
    *   For the ingredient list: In the same "Active Superfood" entry, paste the long text into the **Description** field.
5.  **Footer**: Paste your disclaimer text and "Other ingredients" list here.
