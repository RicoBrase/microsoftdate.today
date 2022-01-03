<script lang="ts">
    const beginOfEra = new Date(2021, 11, 31);
    const todayDate = new Date();

    const dateDiffInDays = Math.floor(
        (todayDate.getTime() - beginOfEra.getTime())
        / 1000 // convert to seconds
        / 60 // convert to minutes
        / 60 // convert to hours
        / 24 // convert to days 
        );

    // plus one, since 2022-01-01 should be equal to 2021-12-33
    let msDateDay = beginOfEra.getDate() + dateDiffInDays + 1;
    let msDateMonth = 12;

    while(msDateDay > 99) { 
        msDateDay -= 99;
        msDateMonth += 1;
    }
    
    /* Since Javascript dates automatically change months, years, etc.
     * if the date gets too big for the current month (e.g. 2021-12-32 <=> 2022-01-01),
     * we need to write a custom formatting function.
     * 
     * Here, we utilize the native formatting to format the date according to the users locale,
     * without being limited by the aforementionend wrapping in the Date objects. */
    function formatDateWithDefaultBrowserLocale(year: number, month: number, day: number): string {
        const dateToGetPatternFrom = new Date("2022-01-01");
        const localeParts = (new Intl.DateTimeFormat().formatToParts(dateToGetPatternFrom));
        return localeParts.map(({type, value}) => {
            switch(type) {
                case 'year':
                    const yearStr = year.toString();
                    return yearStr.substring(yearStr.length - value.length, value.length);
                case "month":
                    if(isNaN(parseFloat(value))) return convertNumberToStringWithLeadingZeroIfNeccessary(month);
                    if(value.length === 1) return month;

                    return convertNumberToStringWithLeadingZeroIfNeccessary(month);
                case "day":
                    if(isNaN(parseFloat(value))) return convertNumberToStringWithLeadingZeroIfNeccessary(day);
                    if(value.length === 1) return day;

                    return convertNumberToStringWithLeadingZeroIfNeccessary(day);
                case "literal":
                    return value;
                default: return "";
            }
        }).join("");
    }

    /* Sometimes, we need to display dates with leading zeros. */
    function convertNumberToStringWithLeadingZeroIfNeccessary(input: number): string {
        return `${input < 10 && input > 0 ? "0" : ""}${input}`;
    }

    const formattedMsDate = formatDateWithDefaultBrowserLocale(2021, msDateMonth, msDateDay);

</script>

{formattedMsDate}
