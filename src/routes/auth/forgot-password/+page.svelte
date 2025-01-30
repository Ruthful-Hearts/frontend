<script lang="ts">
    import * as Card from "$lib/components/ui/card";
    import { Button } from "$lib/components/ui/button";
    import { Input } from "$lib/components/ui/input";
    import { Label } from "$lib/components/ui/label";
    import { goto } from "$app/navigation";

    let email = "";
    let isSubmitted = false;

    async function handleSubmit() {
        // TODO: Implement password reset logic
        console.log("Password reset requested for:", email);
        isSubmitted = true;
    }
</script>

<div class="min-h-screen flex items-center justify-center ">
    <Card.Root class="w-[400px]">
        <Card.Header>
            <Card.Title class="text-2xl font-bold text-center">Reset Password</Card.Title>
            <Card.Description class="text-center">
                Enter your email and we'll send you instructions to reset your password
            </Card.Description>
        </Card.Header>
        <Card.Content>
            {#if !isSubmitted}
                <form on:submit|preventDefault={handleSubmit} class="space-y-4">
                    <div class="space-y-2">
                        <Label for="email">Email</Label>
                        <Input 
                            id="email"
                            type="email" 
                            placeholder="Enter your email"
                            bind:value={email}
                            required
                        />
                    </div>

                    <Button type="submit" class="w-full bg-pink-600 hover:bg-pink-700">
                        Send Reset Link
                    </Button>

                    <div class="text-center text-sm">
                        Remember your password?
                        <button 
                            type="button"
                            class="text-pink-600 hover:underline ml-1"
                            on:click={() => goto('/auth/login')}
                        >
                            Back to login
                        </button>
                    </div>
                </form>
            {:else}
                <div class="space-y-4">
                    <div class="text-center text-green-600">
                        ✓ Reset instructions sent
                    </div>
                    <p class="text-center text-sm text-gray-600">
                        If an account exists for {email}, you will receive password reset instructions in your email.
                    </p>
                    <Button 
                        type="button" 
                        variant="outline" 
                        class="w-full"
                        on:click={() => goto('/auth/login')}
                    >
                        Return to login
                    </Button>
                </div>
            {/if}
        </Card.Content>
    </Card.Root>
</div>
