# P11 Components

P11 documents are React modules that export a default component and use only document-safe components from `@p11/components`.

## Basic Document

```tsx
import { Document, Heading, Section, Text } from "@p11/components";

export default function Proposal() {
  return (
    <Document>
      <Section>
        <Heading level={1}>Proposal</Heading>
        <Text>Write the document body here.</Text>
      </Section>
    </Document>
  );
}
```

## Supported Exports

```txt
Document
Page
Section
Heading
Text
List
ListItem
DefinitionList
DefinitionTerm
DefinitionDescription
Quote
Strikethrough
CodeBlock
Table
TableHeader
TableBody
TableRow
TableHead
TableCell
Figure
Caption
Divider
PageBreak
code
```

Use `code` with `CodeBlock` for readable multiline snippets:

```tsx
import { CodeBlock, Document, Section, code } from "@p11/components";

export default function Notes() {
  return (
    <Document>
      <Section>
        <CodeBlock language="typescript">
          {code`
            const published = await publish({
              input: "./proposal.tsx"
            });
          `}
        </CodeBlock>
      </Section>
    </Document>
  );
}
```

Supported code languages include TypeScript, JavaScript, Python, Rust, HTML/XML, CSS, JSON, YAML, and Bash. `language-*` and `lang-*` class names are recognized.

## Layout

`Document` accepts `mode?: "page" | "pageless"`.

```tsx
<Document mode="pageless">...</Document>
<Document mode="page">...</Document>
```

Pageless is the default screen view. Page mode shows letter-sized page boxes. Print output is paginated either way.

Use `<PageBreak />` to force a new page.

## Tables

```tsx
import {
  Document,
  Section,
  Table,
  TableBody,
  TableCell,
  TableHead,
  TableHeader,
  TableRow
} from "@p11/components";

export default function Summary() {
  return (
    <Document>
      <Section>
        <Table>
          <TableHeader>
            <TableRow>
              <TableHead>Area</TableHead>
              <TableHead>Status</TableHead>
            </TableRow>
          </TableHeader>
          <TableBody>
            <TableRow>
              <TableCell>Launch</TableCell>
              <TableCell>Ready</TableCell>
            </TableRow>
          </TableBody>
        </Table>
      </Section>
    </Document>
  );
}
```

## Do Not Use

Do not import or render app/control components such as:

```txt
Alert
Badge
Button
Card
CardHeader
CardTitle
CardDescription
CardContent
Separator
Stack
Tabs
TabsContent
TabsList
TabsTrigger
Accordion
AccordionContent
AccordionItem
AccordionTrigger
```

Do not use native interactive tags inside authored content:

```txt
button
input
select
textarea
form
nav
```

P11 output should read like a document, not an application screen.
