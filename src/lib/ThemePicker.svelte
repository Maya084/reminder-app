<script lang="ts"></script>

<main>
    <form class="color-picker">
        <fieldset>
            <legend class="visually-hidden">Pick a color cheme</legend>
            <label for="light" class="visually-hidden"> Light </label>
            <input type="radio" name="theme" id="light" checked />
            <label for="dark" class="visually-hidden"> Dark </label>
            <input type="radio" name="theme" id="dark" />
            <label for="pink" class="visually-hidden"> Pink </label>
            <input type="radio" name="theme" id="pink" />
            <label for="mint" class="visually-hidden"> Mint </label>
            <input type="radio" name="theme" id="mint" />
            <label for="autumn" class="visually-hidden"> Autumn </label>
            <input type="radio" name="theme" id="autumn" />
        </fieldset>
    </form>
</main>

<style>
    .visually-hidden {
        clip: rect(0, 0, 0, 0);
        clip-path: inset(50%);
        height: 1px;
        width: 1px;
        overflow: hidden;
        position: absolute;
        white-space: nowrap;
    }

    .color-picker {
        position: fixed;
        top: 0;
        left: 50%;
        transform: translateX(-50%);
    }

    .color-picker > fieldset {
        border: 0;
        display: flex;
        gap: 3rem;
        background-color: var(--section-bg-color);
        width: fit-content;
        padding: 1rem 3rem;
        border-radius: 0 0 1rem 1rem;
    }

    .color-picker input[type="radio"] {
        appearance: none;
        height: 1.5rem;
        width: 1.5rem;
        outline: 3px solid var(--radio-color, currentColor);
        outline-offset: 3px;
        border-radius: 50%;
    }

    input[type="radio"]:checked {
        background-color: var(--radio-color);
    }

    input[type="radio"]#light {
        --radio-color: #fefefe;
    }
    input[type="radio"]#dark {
        --radio-color: #213547;
    }
    input[type="radio"]#pink {
        --radio-color: #b15353;
    }
    input[type="radio"]#mint {
        --radio-color: #3eb489;
    }
    input[type="radio"]#autumn {
        --radio-color: #336B87;
    }
</style>
