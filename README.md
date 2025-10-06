# Bulk Insertion of Questions to Moodle in XML Format

## Multiple-choice question (with single correct answer)

```
<question type="multichoice">

    <name>
        <text>Week_XX_SC_F25</text>
    </name>

    <questiontext format="html">
        <text>Question text</text>
    </questiontext>

    <answer fraction="0">
        <text>The first answer that is incorrect</text>
    </answer>

    <answer fraction="0">
        <text>The second answer that is incorrect</text>
    </answer>

    <answer fraction="0">
        <text>The third answer that is incorrect</text>
    </answer>

    <answer fraction="100">
        <text>The fourth answer that is correct</text>
    </answer>

    <shuffleanswers>1</shuffleanswers>
    <single>true</single>
    <answernumbering>abc</answernumbering>

</question>
```

### Instructions

* Rename `XX` in the question name to match the week number for this question. **Always use two digits**. For example, use `Week_01` instead of `Week_1`.  

* The `fraction` attribute represents the percentage of the total grade allocated to a specific answer. Ensure that the correct answer has a fraction value of `100`, while all other options have a fraction value of `0`.  

* If answer shuffling is explicitly **not allowed**, change the `<shuffleanswers>` value from `1` to `0`. Otherwise, leave it unchanged. Shuffling is typically disabled when the last option is “All of the above” or similar.  

* Do **not** modify the `<single>` and `<answernumbering>` tags.  

* To customize the question statement format, refer to the last section of this document.

## Multiple-choice question (with multiple correct answers)

```
<question type="multichoice">

    <name>
        <text>Week_XX_MC_F25</text>
    </name>

    <questiontext format="html">
        <text>Question text</text>
    </questiontext>

    <answer fraction="-50">
        <text>The first answer that is incorrect</text>
    </answer>

    <answer fraction="-50">
        <text>The second answer that is incorrect</text>
    </answer>

    <answer fraction="50">
        <text>The third answer that is correct</text>
    </answer>

    <answer fraction="50">
        <text>The fourth answer that is correct</text>
    </answer>

    <shuffleanswers>1</shuffleanswers>
    <single>false</single>
    <answernumbering>abc</answernumbering>

</question>
```

### Instructions

* Rename `XX` in the question name to match the week number for this question. **Always use two digits**. For example, use `Week_01` instead of `Week_1`.  

* The `fraction` attribute represents the percentage of the total grade allocated to a specific answer. Ensure that the sum of fractions for all correct options equals `100`, and the sum of fractions for all incorrect options equals `-100`.  

* If answer shuffling is explicitly **not allowed**, change the `<shuffleanswers>` value from `1` to `0`. Otherwise, leave it unchanged. Shuffling is typically disabled when the last option is “All of the above” or similar.  

* Do **not** modify the `<single>` and `<answernumbering>` tags.  

* To customize the question statement format, refer to the last section of this document.

## Matching question

**Please note that the XML import format supports only N-to-N matching questions.**

```
<question type="matching">

    <name>
        <text>Week_XX_Match_F25</text>
    </name>
    
    <questiontext format="html">
        <text>Question statement</text>
    </questiontext>

    <subquestion>
        <text>Option 1</text>
        <answer>
            <text>Correct answer for Option 1</text>
        </answer>
    </subquestion>

    <subquestion>
        <text>Option 2</text>
        <answer>
            <text>Correct answer for Option 2</text>
        </answer>
    </subquestion>

    <shuffleanswers>true</shuffleanswers>

</question>
```

### Instructions

* Rename `XX` in the question name to match the week number for this question. **Always use two digits**. For example, use `Week_01` instead of `Week_1`.  

* Do **not** modify the `<shuffleanswers>`.  

* To customize the question statement format, refer to the last section of this document.

## Formating questions statement

If you want to format a question statement, wrap the content of the question text in `<![CDATA[` and `]]>` tags. This allows you to use HTML formatting, such as `<b>` for bold text, `<i>` for italic text, and `<tt>` for monospace text. 

Please check the following example:

```
<questiontext format="html">
    <text>
        <![CDATA[
            Question text<br />
            <tt>TEXT</tt><br />
            one line<br />
            <i>italic</i><br />
            <b>bold</b><br />
            test
        ]]>
    </text>
</questiontext>
```




