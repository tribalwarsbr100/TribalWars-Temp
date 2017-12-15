(function ()
{
        function getServerTime()
        {
                var d = $('#serverDate')
                        .text()
                        , t = $('#serverTime')
                        .text()
                        , m = d.match(/(..)\/(..)\/(....)/);
                return m[3] + '-' + m[2] + '-' + m[1] + ' ' + t
        }

        function getServerMs(zeroMs)
        {
                var currMs = new Date()
                        .getMilliseconds();
                return (1000 + currMs - zeroMs) % 1000
        }

        function getServerTimeWithMs(zeroMs)
        {
                return getServerTime() + ':' + getServerMs(zeroMs)
        }

        function displayServerMs(z)
        {
                var msTimer = setInterval(function ()
                {
                        var ms = getServerMs(z);
                        $('#serverMs')
                                .text(':' + ('00' + ms)
                                        .substr(-3))
                }, 5);
                return msTimer
        }
        if (!$('#serverMs')
                .length)
        {
                $('#serverTime')
                        .after('<span id="serverMs"></span>')
        }
        var serverTime = getServerTime()
                , prev = serverTime;
        var localMs;
        var timer = setInterval(function ()
        {
                serverTime = getServerTime();
                if (serverTime !== prev)
                {
                        localMs = new Date()
                                .getMilliseconds();
                        clearInterval(timer);
                        displayServerMs(localMs)
                }
                prev = serverTime
        }, 100);
        $('#serverMs')
                .css(
                {
                        'font-size': '20pt'
                        , 'color': '#0000A5'
                        , 'serif': 'sans_serif'
                });
        $('#serverTime')
                .css(
                {
                        'font-size': '15pt'
                        , 'color': '#000'
                        , 'serif': 'sans_serif'
                })
})();
