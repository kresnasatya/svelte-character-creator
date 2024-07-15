<script>
    import Character from "./components/Character.svelte";
    import ControlPane from "./components/ControlPane.svelte";
    import MaxWidthWrapper from "./components/MaxWidthWrapper.svelte";

    import { headOptions, faceOptions, bodyOptions, skinColorOptions, clothesColorOptions, accessoryOptions } from "./helpers";
    import { defaultSkinColor, defaultClothesColor } from "./constants";

    let head = 0, face = 0, body = 0, accessory = 0;
    let skinColor = defaultSkinColor, clothesColor = defaultClothesColor;
</script>

<main class="character-editor">
    <MaxWidthWrapper>
        <header class="header">
            <h1 class="title">Create your Character</h1>
            <p class="description">
                Customize your character's look and style using the
                controls below. What sort of adventure will you embark on?{' '}
            </p>
        </header>
        <div class="control-column">
            <ControlPane
                title="Bodies"
                options={bodyOptions}
                currentOption={body}
                on:option={(event) => body = event.detail.option}
            />
            <ControlPane
                title="Heads"
                options={headOptions}
                currentOption={head}
                on:option={(event) => head = event.detail.option}
            />
            <ControlPane
                title="Faces"
                options={faceOptions}
                currentOption={face}
                on:option={(event) => face = event.detail.option}
            />
            <ControlPane
                title="Accessories"
                options={accessoryOptions}
                currentOption={accessory}
                on:option={(event) => accessory = event.detail.option}
            />
            <ControlPane
                title="Skin Color"
                options={skinColorOptions}
                currentOption={skinColor}
                on:option={(event) => skinColor = event.detail.option}
            />
            <ControlPane
                title="Clothing Color"
                options={clothesColorOptions}
                currentOption={clothesColor}
                on:option={(event) => clothesColor = event.detail.option}
            />
        </div>
    </MaxWidthWrapper>
    
    <div class="character-wrapper">
        <Character
            body={body}
            head={head}
            face={face}
            accessory={accessory}
            skinColor={skinColor}
            clothesColor={clothesColor}
        />
    </div>            
</main>

<style>
.character-editor {
    padding-top: 128px;
    padding-bottom: 64px;
}

.header {
    width: 65%;
    padding-bottom: 64px;
}

.title {
    font-size: 2.5rem;
    font-weight: 600;
    margin-top: 0;
    margin-bottom: 16px;
    letter-spacing: -0.5px;
}

.description {
    font-size: 1.25rem;
    margin: 0;
}
</style>